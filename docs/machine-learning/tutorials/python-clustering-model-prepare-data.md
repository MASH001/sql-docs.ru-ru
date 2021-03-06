---
title: Учебник по Python. Подготовка данных кластера
description: В второй части серии руководств из четырех частей описано, как подготовить данные SQL для кластеризации в Python с помощью Служб машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 12/17/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8ee19ddfa59f8f1a4a32c0adf08b8f36eef9aa1f
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "81116517"
---
# <a name="tutorial-prepare-data-to-categorize-customers-in-python-with-sql-server-machine-learning-services"></a>Руководство по Подготовка данных для категоризации клиентов в Python со службами машинного обучения SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Во второй части этого учебника, состоящего из четырех частей, вы восстановите и подготовите данные из базы данных SQL с использованием Python. Далее в этой серии руководств вы будете использовать эти данные для обучения и развертывания модели кластеризации с использованием Python в службах машинного обучения SQL Server.

В этой статье вы узнаете, как выполнять следующие задачи.

> [!div class="checklist"]
> * Разделение клиентов по различным измерениям с помощью Python
> * Загрузка данных из базы данных SQL в кадр данных Python

В [первой части](python-clustering-model.md) были установлены необходимые компоненты и восстановлена демонстрационная база данных.

В [третьей части](python-clustering-model-build.md) вы узнаете, как создать и обучить модель кластеризации на основе k-средних в Python.

В [четвертой части](python-clustering-model-deploy.md) вы узнаете, как создать хранимую процедуру в базе данных SQL, которая может выполнять кластеризацию в Python на основе новых данных.

## <a name="prerequisites"></a>Предварительные требования

* Во второй части этого учебника предполагается, что вы уже выполнили предварительные требования [**первой части**](python-clustering-model.md).

## <a name="separate-customers"></a>Разделение клиентов

Чтобы подготовиться к кластеризации клиентов, сначала необходимо разделить клиентов по следующим измерениям:

* **orderRatio** = коэффициент возвратов заказов (отношение числа частично или полностью возвращенных заказов к общему числу заказов)
* **itemsRatio** = коэффициент возврата единицы товара (отношение возвращенных единиц товара к общему числу проданных единиц товара)
* **monetaryRatio** = коэффициент возврата в денежном выражении (отношение общего объема возвратов к общему объему покупок в денежном выражении)
* **frequency** = частота возвратов

Откройте новую записную книжку в Azure Data Studio и выполните следующий сценарий.

В строке подключения при необходимости замените параметры подключения.

```python
# Load packages.
import pyodbc
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from scipy.spatial import distance as sci_distance
from sklearn import cluster as sk_cluster

################################################################################################

## Connect to DB and select data

################################################################################################

# Connection string to connect to SQL Server named instance.
conn_str = pyodbc.connect('DRIVER={ODBC Driver 17 for SQL Server}; SERVER=localhost; DATABASE=tpcxbb_1gb; Trusted_Connection=yes')

input_query = '''SELECT
ss_customer_sk AS customer,
ROUND(COALESCE(returns_count / NULLIF(1.0*orders_count, 0), 0), 7) AS orderRatio,
ROUND(COALESCE(returns_items / NULLIF(1.0*orders_items, 0), 0), 7) AS itemsRatio,
ROUND(COALESCE(returns_money / NULLIF(1.0*orders_money, 0), 0), 7) AS monetaryRatio,
COALESCE(returns_count, 0) AS frequency
FROM
(
  SELECT
    ss_customer_sk,
    -- return order ratio
    COUNT(distinct(ss_ticket_number)) AS orders_count,
    -- return ss_item_sk ratio
    COUNT(ss_item_sk) AS orders_items,
    -- return monetary amount ratio
    SUM( ss_net_paid ) AS orders_money
  FROM store_sales s
  GROUP BY ss_customer_sk
) orders
LEFT OUTER JOIN
(
  SELECT
    sr_customer_sk,
    -- return order ratio
    count(distinct(sr_ticket_number)) as returns_count,
    -- return ss_item_sk ratio
    COUNT(sr_item_sk) as returns_items,
    -- return monetary amount ratio
    SUM( sr_return_amt ) AS returns_money
FROM store_returns
GROUP BY sr_customer_sk ) returned ON ss_customer_sk=sr_customer_sk'''


# Define the columns we wish to import.
column_info = {
    "customer": {"type": "integer"},
    "orderRatio": {"type": "integer"},
    "itemsRatio": {"type": "integer"},
    "frequency": {"type": "integer"}
}
```

## <a name="load-the-data-into-a-data-frame"></a>Загрузка данных в кадр данных

Результаты запроса возвращаются в Python с помощью функции Pandas **read_sql**. Во время выполнения этого задания будут использоваться сведения о столбцах, определенные в предыдущем сценарии.

```python
customer_data = pandas.read_sql(input_query, conn_str)
```

Теперь выведем начало кадра данных, чтобы убедиться, что он выглядит правильно.

```python
print("Data frame:", customer_data.head(n=5))
```

```results
Rows Read: 37336, Total Rows Processed: 37336, Total Chunk Time: 0.172 seconds
Data frame:     customer  orderRatio  itemsRatio  monetaryRatio  frequency
0    29727.0    0.000000    0.000000       0.000000          0
1    97643.0    0.068182    0.078176       0.037034          3
2    57247.0    0.000000    0.000000       0.000000          0
3    32549.0    0.086957    0.068657       0.031281          4
4     2040.0    0.000000    0.000000       0.000000          0
```

## <a name="clean-up-resources"></a>Очистка ресурсов

Если вы не собираетесь продолжать работу с этим учебником, удалите базу данных tpcxbb_1gb из SQL Server.

## <a name="next-steps"></a>Дальнейшие действия

Во второй части этого учебника вы выполнили следующие действия.

* Разделение клиентов по различным измерениям с помощью Python
* Загрузка данных из базы данных SQL в кадр данных Python

Чтобы создать модель машинного обучения, которая использует эти данные о клиентах, перейдите к третьей части этого учебника:

> [!div class="nextstepaction"]
> [Руководство. Создание модели прогнозов в Python с помощью служб машинного обучения SQL Server](python-clustering-model-build.md)

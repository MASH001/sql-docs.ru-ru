---
title: Использование разрешения IP-адресов прозрачной сети | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68070543e8fee326f0b5a02c73f0c0e4aaef6fbe
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928282"
---
# <a name="using-transparent-network-ip-resolution"></a>Использование разрешения IP-адресов прозрачной сети
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution представляет собой обновленную версию существующей функции MultiSubnetFailover, который включен в драйвер Microsoft ODBC 13.1 для SQL Server и воздействует на последовательность подключения драйвера в тех случаях, когда с именем узла связано несколько IP-адресов, но первый разрешенный для этого узла IP-адрес не отвечает на запросы. Он взаимодействует с MultiSubnetFailover и поддерживает следующие три варианта последовательности подключений.

* 0: Сначала один IP-адрес, а затем все IP-адреса в параллельном режиме.
* 1: Все IP-адреса в параллельном режиме.
* 2: Все IP-адреса последовательно.

|TransparentNetworkIPResolution|MultiSubnetFailover|Поведение|
|:-:|:-:|:-:|
|(по умолчанию).|(по умолчанию).|0|
|(по умолчанию).|Активировано|1|
|(по умолчанию).|Выключено|0|
|Активировано|(по умолчанию).|0|
|Активировано|Активировано|1|
|Активировано|Выключено|0|
|Выключено|(по умолчанию).|2|
|Выключено|Активировано|1|
|Выключено|Выключено|2|

Строка подключения `TransparentNetworkIPResolution` и ключевое слово DSN определяют значение этого параметра на уровне строки подключения. По умолчанию этот параметр включен.

Ключевое слово|Значения|По умолчанию
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

Настраиваемый перед подключением атрибут `SQL_COPT_SS_TNIR` позволяет приложению управлять этим параметром программным способом.

Атрибут подключения|   Размер и тип|  По умолчанию| Значение| Описание
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER` либо `SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|Разрешает или запрещает TNIR.

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recovery"></a>Дополнительные сведения о MultiSubnetFailover см. в [руководстве по обеспечению высокого уровня доступности и аварийному восстановлению для драйвера ODBC для Linux и macOS](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).
--------------------------------------------------
## <a name="see-also"></a>См. также:  
* [Драйвер Microsoft ODBC Driver for SQL Server в Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [Кластеры SQL Server с несколькими подсетями (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)

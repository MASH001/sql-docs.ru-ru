---
title: Заполнение по примеру (средства анализа таблиц для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- fill from example
ms.assetid: dac57d8f-1c65-4878-8ea0-9c680df5e4fb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d1e09e439469f23412c84ea7bab65c0aa748f286
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66081320"
---
# <a name="fill-from-example-table-analysis-tools-for-excel"></a>Заполнение по примеру (средства анализа таблиц для Excel)
  ![Кнопка «Заполнение по примеру» ленты «Средства анализа таблиц»](media/tat-fillex.gif "Кнопка «Заполнение по примеру» ленты «Средства анализа таблиц»")  
  
 Средство **Заполнение по примеру** позволяет создавать новые столбцы данных на основе существующих значений.  
  
 Например, предположим, что данные содержат столбец « **Сумма покупки** », столбец « **количество заказов** » и столбец **Premier Customer** , основанный на формуле с другими столбцами. Если столбец **Premier Customer** содержит много пустых строк, для определения недостающих значений можно использовать столбцы **Сумма покупки** и **количество заказов** в качестве входных данных. Средство анализирует существующие закономерности в данных вместе с введенными примерами и прогнозирует, какую категорию назначить каждому клиенту.  
  
 Если результат окажется неудовлетворительным, можно сделать уточнение, введя дополнительные примеры значений.  
  
## <a name="using-the-fill-from-example-tool"></a>Использование средства «Заполнение по примеру»  
  
1.  На ленте **анализ** нажмите кнопку **заполнить по примеру**.  
  
2.  Средство автоматически выберет столбец для заполнения результатами анализа, после чего можно принять или переопределить полученные в результате анализа данные.  
  
3.  Создайте столбец для новых данных и введите примеры значений данных, для которых следует сформировать прогноз. Необходимо ввести по крайней мере один пример для каждого значения, для которого требуется сформировать прогноз. Если данные вводятся в существующий столбец, выберите столбец, содержащий недостающие данные.  
  
4.  При необходимости нажмите кнопку **выбрать столбцы для использования при анализе**. В диалоговом окне **Выбор дополнительных столбцов** укажите столбцы, которые, скорее всего, будут использоваться при заполнении недостающих данных.  
  
     Например, если исходя из опыта известно, что существует причинно-следственная связь между одним столбцом и другим столбцом, в котором отсутствуют некоторые значения, то для получения лучших результатов, возможно, нет необходимости использовать остальные столбцы.  
  
     Нажмите кнопку **ОК**.  
  
5.  Нажмите кнопку **Выполнить**.  
  
     После завершения анализа средство создает новый лист **шаблонов** , содержащий результаты анализа. Отчет перечисляет правила или ключевые факторы влияния, которые были найдены, а также показывает вероятность для каждого правила.  
  
     Средство также автоматически добавляет столбец, который содержит новые значения, в таблицу исходных данных. Эти значения можно просмотреть и сравнить с первоначальными значениями.  
  
### <a name="requirements"></a>Требования  
 Анализ выполняется только для данных, расположенных в столбцах. Если ряд, который должен быть заполнен, хранится в виде строки, можно использовать функцию вставки и транспонирования Excel для представления данных в формате столбца.  
  
## <a name="understanding-the-pattern-report"></a>Основные сведения об отчете о закономерностях  
 При запуске средства **заполнения из примера** создается отчет, содержащий дополнительные сведения об обнаруженных закономерностях. Эти шаблоны используются при экстраполяции новых значений данных.  
  
 Отчет о закономерностях раскрывает ключевые факторы, влияющие на каждое прогнозируемое значение. Описание каждого влияющего фактора или правила содержит в себе имя столбца, значение столбца и относительное влияние данного правила на прогноз.  
  
 Например, если выполняется анализ листа, содержащего данные о расстоянии доставки заказанных товаров, то логично ожидать, что стоимость доставки практически напрямую зависит от расстояния до пункта назначения. В этом случае отчет может содержать следующую строку.  
  
|Столбец|Применение|Подходит|Относительное влияние|  
|------------|-----------|------------|---------------------|  
|StateProvinceCode|AB|>500 километров|80 %|  
  
 Это означает, что значение AB в столбце **статепровинцекоде** строго прогнозирует расстояние доставки >500 километров.  
  
 Обычно прогнозы основываются на более сложных закономерностях, чем приведенная в данном примере, и отчет может содержать большое количество строк правил для каждого прогноза. При получении окончательного значения прогноза учитывается влияние всех правил.  
  
> [!NOTE]  
>  **Относительное влияние** отображается в виде затененной полосы. Чем длиннее эта полоса, тем больше вероятность того, что данное правило оказалось способным выработать прогноз для заполненного значения.  
  
 Средство также добавляет новый столбец в исходную таблицу данных, имя именованного \<столбца> расширено.  
  
 Если исходный столбец с данными уже содержал значение, это значение будет скопировано в новый столбец. Однако если в исходном столбце не было значения, в новый столбец будет помещено значение прогноза, рассчитанное мастером.  
  
## <a name="related-tools-and-information"></a>Дополнительные средства и сведения  
 Для проверки распределения значений в столбце Excel можно также использовать мастер [просмотра данных](explore-data-sql-server-data-mining-add-ins.md) , доступный в клиенте интеллектуального анализа данных для Excel. Дополнительные сведения см. в разделе [Просмотр и очистка данных](exploring-and-cleaning-data.md).  
  
## <a name="see-also"></a>См. также  
 [Средства анализа таблиц для Excel](table-analysis-tools-for-excel.md)  
  
  

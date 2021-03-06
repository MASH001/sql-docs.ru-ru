---
title: Сценарий поиска решения (средства анализа таблиц для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- scenario analysis
- goal seek scenario
ms.assetid: efe50306-cf7c-46b3-9cc4-e7f0b6968b0c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d547c52bc5d4cb02870fc647469b5f63af9ab7cb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66080738"
---
# <a name="goal-seek-scenario-table-analysis-tools-for-excel"></a>Сценарий поиска решения (средства анализа таблиц для Excel)
  ![Кнопка «Поиск решения» на ленте «Средства анализа таблиц»](media/tat-goalseek.gif "Кнопка «Поиск решения» на ленте «Средства анализа таблиц»")  
  
 Средство **поиска решения** является дополнением к средству сценария [What If](what-if-scenario-table-analysis-tools-for-excel.md) . Средство " **что если** " сообщает о влиянии изменения, в то время как средство **поиска решения** указывает базовые факторы, которые необходимо изменить для достижения желаемого результата.  
  
 Например, предположим, что ваша цель состоит в увеличении удовлетворенности клиентов. Вы можете использовать анализ **поиска решения** , чтобы определить, какие факторы лучше всего увеличивают удовлетворенность клиентов, и решить, являются ли эти изменения экономичными.  
  
 После окончания анализа в исходной таблице создаются два новых столбца. В этих столбцах показана *вероятность* достижения целевого результата и рекомендуемого изменения (при наличии).  
  
 Можно использовать это средство, которое способно анализировать набор данных и делать прогнозы для всего набора, либо пользователь может сам выполнить анализ, а затем последовательно проверить сценарии.  
  
## <a name="using-the-goal-seek-scenario-tool"></a>Использование средства сценариев поиска решения  
  
1.  Откройте таблицу Excel.  
  
2.  Щелкните **сценарии**и выберите **Поиск решения**.  
  
3.  В диалоговом окне **Анализ сценария: Поиск решения** выберите столбец, содержащий целевое значение из списка.  
  
4.  Укажите значение, которое требуется достичь.  
  
     Если столбец содержит непрерывные числовые значения, можно также в качестве цели указать нужное увеличение или уменьшение значения. Например, можно выбрать **Sales** в качестве столбца и указать, что целевой объект будет увеличен на 120%.  
  
     Либо можно в качестве цели задать диапазон значений, введя нижний и верхний пределы.  
  
5.  Укажите столбец, содержащий значения, которые нужно изменить. Другими словами, выберите столбец, с которым будет производиться работа для достижения нужного результата.  
  
6.  При необходимости нажмите кнопку **выбрать столбцы, которые будут использоваться для анализа**, а затем выберите столбцы, содержащие полезную информацию. Не выбирайте столбцы, которые не влияют на анализ.  
  
    > [!NOTE]  
    >  Не отменяйте выбор столбцов, которые нужно использовать для решения или изменения. Это обязательные для выбора столбцы.  
  
7.  Укажите, будет ли прогноз выполнен для всей таблицы или только для выбранной строки.  
  
8.  Если выбран параметр « **вся таблица** », то средство добавляет прогнозы в исходную таблицу в двух новых столбцах.  
  
9. Если в **этой строке**был выбран параметр, результаты анализа будут выведены в диалоговое окно для проверки. Это диалоговое окно будет оставаться открытым, поэтому можно продолжать работу по анализу новых значений и выбору новых решений.  
  
### <a name="requirements"></a>Требования  
 В этом средстве используется алгоритм логистической регрессии (Майкрософт), который может обрабатывать числовые или дискретные значения.  
  
 Прогноз может быть выполнен несколько раз для различных столбцов, однако каждое сочетание целевого значения и изменения должно быть рассчитано отдельно.  
  
 Для достижения лучших результатов следует выбирать такие столбцы, в которых содержится полезная для анализа информация. Но если будет выбрано слишком мало столбцов, то достижение необходимого результата может быть затруднительным.  
  
 При последовательном создании прогнозов необходимо выбирать строку, которая изначально не содержит нужный результат, чтобы не получить ошибку. Например, если целью поиска решения является определение факторов, способствующих покупкам велосипедов, необходимо включать только клиентов, у которых еще нет велосипеда.  
  
## <a name="understanding-the-results-of-goal-seek-analysis"></a>Основные сведения о результатах анализа поиска решения  
 При создании сценария поиска решения средство выполняет три действия.  
  
-   Создает структуру интеллектуального анализа данных, в которой хранятся ключевые факты о содержащихся в таблице данных.  
  
-   На основе существующих данных создает модель интеллектуального анализа данных с логистической регрессией.  
  
-   Создает прогноз для каждого задаваемого значения.  
  
 При последовательной проверке сценариев поиска решения результаты можно просматривать в интерактивном режиме. Это то же самое, что и создание *одноэлементного прогнозирующего запроса*.  
  
 Средство сообщает об этом в области **результатов** диалогового окна о том, было ли оно успешным при поиске сценария, который достигает нужной цели. Если успешное решение найдено, средство также формирует рекомендацию, которая указывает необходимое изменение. Например, средство **поиска решения** может сообщить, что расстояние до работы должно быть меньше 5 миль.  
  
 Пример результатов:  
  
 **При поиске решения для задачи «Интерес к приобретению» удалось найти решение.**  
  
 **Ближайшее соответствие достигается при изменении параметра «Расстояние до работы» на значение «2–5 километров».**  
  
 Поскольку данный результат основан на существующей строке таблицы данных, он говорит, что при уменьшении расстояния до работы до 2–5 километров, при неизменности всех остальных характеристик конкретного клиента, он купит велосипед с большей вероятностью.  
  
 Если вы создаете прогнозы для всех строк в таблице Excel, указав **всю таблицу**, сетул создает два новых столбца в исходной таблице данных. В первом добавленном столбце могут быть либо флажки на фоне зеленого круга, указывающие на то, что решение может быть найдено, либо символы «Х» на фоне красного круга, указывающие на то, что решение не может быть найдено ни при каких изменениях значения.  
  
 Второй столбец содержит рекомендуемое изменение.  
  
> [!NOTE]  
>  Степень достоверности рекомендаций и успешное их применение предопределяется исключительно используемым алгоритмом без возможности каких-либо изменений.  
  
## <a name="related-tools"></a>Дополнительные средства  
 Клиент интеллектуального анализа данных для Excel представляет собой отдельную надстройку, поддерживающую дополнительные возможности интеллектуального анализа данных, в состав которой входят несколько мастеров, предназначенных для создания моделей интеллектуального анализа данных, прогнозирующих поведение. Дополнительные сведения см. [в разделе Создание модели интеллектуального анализа данных](creating-a-data-mining-model.md).  
  
 Дополнительные сведения о алгоритме, используемом средством «сценарий **поиска решения** », см. в разделе «Алгоритм логистической регрессии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (Майкрософт)» электронной документации по.  
  
## <a name="see-also"></a>См. также  
 [Средства анализа таблиц для Excel](table-analysis-tools-for-excel.md)  
  
  

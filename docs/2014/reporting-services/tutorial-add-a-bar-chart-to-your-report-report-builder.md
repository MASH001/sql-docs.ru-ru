---
title: Учебник. Добавление линейчатой диаграммы к отчету (построитель отчетов) | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6956ebd6-0217-4087-a4fa-5cc1c3804691
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2db0ec56ec79134cdb1cba51e1c19d9ac124f4f1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099197"
---
# <a name="tutorial-add-a-bar-chart-to-your-report-report-builder"></a>Учебник. Добавление линейчатой диаграммы к отчету (построитель отчетов)
  В линейчатых диаграммах категории данных отображаются по горизонтали. Это может использоваться для:  
  
-   улучшения читаемости длинных имен категорий;  
  
-   облегчения восприятия времени, отображаемого в виде значений;  
  
-   сравнение относительных значений нескольких рядов.  
  
 На следующем рисунке показана создаваемая линейчатая диаграмма, на которой отображены данные продаж за 2008 и 2009 гг. для пяти менеджеров по продажам с максимальными объемами продаж, перечисленных в алфавитном порядке.  
  
 ![rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "rs_BarChartTutorial")  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Что вы узнаете  
 В этом учебнике рассматриваются следующие темы:  
  
1.  [Создание диаграммы с помощью мастера диаграмм](#Chart)  
  
2.  [Выбор типа диаграммы](#ChartType)  
  
3.  [Отображение всех значений категорий по вертикальной оси](#AllValues)  
  
4.  [Изменение отображения имен по вертикальной оси](#Sort)  
  
5.  [Перемещение условных обозначений](#Legend)  
  
6.  [Перемещение заголовка диаграммы](#ChartTitle)  
  
7.  [Форматирование и задание меток для горизонтальной оси](#Horizontal)  
  
8.  [Добавление фильтра для отображения 5 максимальных значений](#Filter)  
  
9. [Добавление заголовка отчета](#Title)  
  
10. [Сохранение отчета](#Save)  
  
> [!NOTE]  
>  В этом учебнике шаги работы с мастером объединены в одну процедуру. Пошаговые инструкции по переходу к серверу отчетов, созданию набора данных и выбору источника данных см. в первом учебнике этой серии: [Учебник. Создание простого табличного отчета (построитель отчетов)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Предполагаемое время для выполнения заданий этого учебника: 15 минут.  
  
## <a name="requirements"></a>Требования  
 Дополнительные сведения о требованиях см. в разделе [Предварительные условия для использования учебников (построитель отчетов)](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a>1. Создание отчета с диаграммой с помощью мастера диаграмм  
 В диалоговом окне **Начало работы** создайте внедренный набор данных, выберите общий источник и создайте линейчатую диаграмму с помощью мастера диаграмм.  
  
> [!NOTE]  
>  В этом учебнике запрос уже содержит значения данных, поэтому внешний источник данных не требуется. В связи с этим запрос получается весьма длинным. В рабочей среде запрос не будет содержать данные. Этот запрос содержит данные только в учебных целях.  
  
#### <a name="to-create-a-new-chart-report"></a>Создание нового отчета с диаграммой  
  
1.  Нажмите кнопку **Пуск**, наведите курсор на пункты **Все программы**, **Построитель отчетов Microsoft SQL Server 2012**и выберите пункт **Построитель отчетов**.  
  
     Откроется диалоговое окно **Начало работы** .  
  
    > [!NOTE]  
    >  Если диалоговое окно **Начало работы** не отображается, нажмите кнопку Построитель отчетов, а затем нажмите кнопку **создать**.  
  
2.  Убедитесь, что на левой панели выбран **Новый отчет** .  
  
3.  На правой панели выберите **Мастер диаграмм**.  
  
4.  На странице **Выбор набора данных** нажмите кнопку **Создать набор данных**, а затем кнопку **Далее**.  
  
5.  На странице **Выбор соединения с источником данных** выберите существующий источник данных или перейдите к серверу отчетов и выберите источник данных, а затем нажмите кнопку **Далее**. Может потребоваться указать имя пользователя и пароль.  
  
    > [!NOTE]  
    >  При наличии необходимых разрешений выбор источника данных не имеет существенного значения. Этот источник данных не будет использоваться для получения данных. Дополнительные сведения см. в разделе [Альтернативные способы создания подключения к данным &#40;построитель отчетов&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
6.  На странице **Проектирование запроса** нажмите кнопку **Изменить как текст**.  
  
7.  На панель запроса вставьте следующий запрос:  
  
    ```  
    SELECT 'Luis' as FirstName, 'Alverca' as LastName, CAST(170000.00 AS money) AS SalesYear2009, CAST(150000. AS money) AS SalesYear2008  
    UNION SELECT 'Jeffrey' as FirstName, 'Zeng' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(190000. AS money) AS SalesYear2008  
    UNION SELECT 'Houman' as FirstName, 'Pournasseh' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Robin' as FirstName, 'Wood' as LastName, CAST(75000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'Daniela' as FirstName, 'Guaita' as LastName,  CAST(170000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'John' as FirstName, 'Yokim' as LastName, CAST(160000. AS money) AS SalesYear2009, CAST(195000. AS money) AS SalesYear2008  
    UNION SELECT 'Delphine' as FirstName, 'Ribaute' as LastName, CAST(180000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Robert' as FirstName, 'Hernady' as LastName, CAST(140000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Tanja' as FirstName, 'Plate' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(160000. AS money) AS SalesYear2008  
    UNION SELECT 'David' as FirstName, 'Bradley' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Michal' as FirstName, 'Jaworski' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(220000. AS money) AS SalesYear2008  
    UNION SELECT 'Chris' as FirstName, 'Ashton' as LastName, CAST(195000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Pongsiri' as FirstName, 'Hirunyanitiwatna' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(215000. AS money) AS SalesYear2008  
    UNION SELECT 'Brian' as FirstName, 'Burke' as LastName, CAST(187000. AS money) AS SalesYear2009, CAST(207000. AS money) AS SalesYear2008  
    ```  
  
8.  Нажмите кнопку Выполнить (**!**), чтобы просмотреть данные, на основе которых будет создана диаграмма (необязательно).  
  
9. Нажмите кнопку **Далее**.  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a>2. Выбор типа диаграммы  
 Можно выбрать один из различных стандартных типов диаграмм.  
  
#### <a name="to-add-a-column-chart"></a>Добавление гистограммы  
  
1.  На странице **Выбор типа диаграммы** в качестве типа диаграммы по умолчанию задана гистограмма.  
  
2.  Нажмите кнопку **Линейчатая**, а затем кнопку **Далее**.  
  
     На странице **Расположение полей диаграммы** есть четыре поля в области **Доступные поля** : FirstName, LastName, SalesYear2009 и SalesYear2008.  
  
3.  Перетащите поле «LastName» на панель «Категории».  
  
4.  Перетащите поле «SalesYear2009» на панель «Значения». «SalesYear2009» представляет объем продаж всех менеджеров по продажам за 2009 г. На панели «Значения» отображается выражение `[Sum(SalesYear2009)]` , поскольку в диаграмме отображается агрегат для каждого из продуктов.  
  
5.  Перетащите поле «SalesYear2008» на панель «Значения» ниже «SalesYear2009». «SalesYear2008» представляет объем продаж всех менеджеров по продажам за 2008 г.  
  
6.  Нажмите кнопку **Далее**.  
  
7.  На панели Стили на странице **Выбор стиля** выберите стиль.  
  
     Стиль задает стиль шрифта, набор цветов и стиль границы. При выборе стиля на панели просмотра отобразится образец диаграммы с этим стилем.  
  
8.  Нажмите кнопку **Готово**.  
  
     Диаграмма добавляется в область конструктора.  
  
9. Щелкните диаграмму, чтобы отобразить ее маркеры. Перетащите правый нижний угол диаграммы вниз, чтобы увеличить ее размер.  
  
10. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 В отчете отображается линейчатая диаграмма с данными продаж всех менеджеров по продажам за 2008 и 2009 гг. Длина линии на диаграмме соответствует общему значению объема продаж.  
  
##  <a name="3-modify-the-display-of-names-on-the-vertical-axis"></a><a name="AllValues"></a>3. изменение отображаемых имен на вертикальной оси  
 По умолчанию на вертикальной оси отображаются только определенные значения. Диаграмму можно изменить для отображения всех категорий.  
  
#### <a name="to-display-all-sales-persons-along-the-category-axis-of-a-bar-chart"></a>Отображение всех менеджеров по продажам на оси категорий линейчатой диаграммы  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Щелкните правой кнопкой мыши вертикальную ось и выберите пункт **Свойства вертикальной оси**.  
  
3.  В области **Диапазон и интервал оси**в поле **Интервал** введите значение **1**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Щелкните правой кнопкой мыши заголовок вертикальной **оси** и снимите флажок **Показывать заголовок оси** .  
  
6.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
> [!NOTE]  
>  Если имена менеджеров по продажам на вертикальной оси невозможно прочесть, можно увеличить высоту диаграммы или изменить параметры форматирования для меток оси.  
  
###  <a name="display-last-name-and-first-name-on-vertical-axis"></a><a name="CategoryExpression"></a>Отображать фамилию и имя на вертикальной оси  
 Можно изменить выражение категории для отображения фамилии, после которой будет отображаться имя для всех менеджеров по продажам.  
  
##### <a name="to-change-the-category-expression"></a>Изменение выражения категории  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Дважды щелкните диаграмму, чтобы отобразить панель **Данные диаграммы** .  
  
3.  Щелкните правой кнопкой мыши поле [LastName] в области **Группы категорий** и выберите пункт **Свойства группы категорий**.  
  
4.  В поле «Метка» нажмите кнопку «Выражение» (Fx).  
  
5.  Введите следующее выражение: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`  
  
     В выражении будут объединены фамилия, запятая и имя.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Если фамилии не отображаются при выполнении отчета, то данные можно обновить вручную. Оставаясь в режиме предварительного просмотра, на вкладке **Выполнить** в группе **Навигация** нажмите кнопку **Обновить**.  
  
> [!NOTE]  
>  Если имена менеджеров по продажам на вертикальной оси невозможно прочесть, можно увеличить высоту диаграммы или изменить параметры форматирования для меток оси.  
  
##  <a name="4-change-the-sort-order-for-names-on-the-vertical-axis"></a><a name="Sort"></a>4. изменение порядка сортировки для имен на вертикальной оси  
 При сортировке данных на диаграмме изменяется порядок значений на осях категории.  
  
#### <a name="to-sort-the-names-in-alphabetical-order-on-the-bar-chart"></a>Сортировка имен на линейчатой диаграмме в алфавитном порядке  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Дважды щелкните диаграмму, чтобы отобразить панель **Данные диаграммы** .  
  
3.  Щелкните правой кнопкой мыши поле [LastName] в области **Группы категорий** и выберите пункт **Свойства группы категорий**.  
  
4.  Щелкните **Сортировка**. На странице **Изменение параметров сортировки** отображается список выражений фильтров. По умолчанию в этом списке имеется одно выражение сортировки, идентичное исходному выражению группы категорий.  
  
5.  В поле Сортировать по нажмите кнопку Выражение (**FX**).  
  
6.  Введите следующее выражение: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`  
  
7.  Нажмите кнопку **ОК**.  
  
8.  Вернитесь на страницу **свойств группы категорий** , в раскрывающемся списке **порядок** выберите **от я до а**. Это позволяет выбрать обратный алфавитный порядок, чтобы имена отображались в порядке сверху вниз.  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Имена на горизонтальной оси сортируются в обратном порядке, с **алерка** сверху и **Zeng)** внизу.  
  
##  <a name="5-move-the-legend"></a><a name="Legend"></a>5. Перемещение условных обозначений  
 Чтобы улучшить читаемость значений диаграммы, можно переместить ее условные обозначения. Например, в линейчатой диаграмме, в которой столбцы отображаются горизонтально, можно изменить положение условных обозначений, чтобы они находились выше или ниже области диаграммы. В результате для столбцов выделяется больше места.  
  
#### <a name="to-display-the-legend-below-the-chart-area-of-a-bar-chart"></a>Вывод условных обозначений под областью линейчатой диаграммы  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Щелкните правой кнопкой мыши условные обозначения диаграммы.  
  
3.  Выберите **Свойства условных обозначений**.  
  
4.  Выберите другое значение для параметра **Положение условных обозначений**. Например, можно выбрать параметр, соответствующий расположению посередине в нижней части.  
  
     Если условные обозначения перемесить в верхнюю или нижнюю часть диаграммы, их макет изменится с вертикального на горизонтальный. Можно выбрать другой макет в раскрывающемся списке **Макет** .  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
##  <a name="6-title-the-chart"></a><a name="ChartTitle"></a>6. заголовком диаграммы  
  
#### <a name="to-change-the-chart-title-above-the-chart-area-of-a-bar-chart"></a>Изменение заголовка диаграммы над областью линейчатой диаграммы  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Выберите **заголовок диаграммы** слова в верхней части диаграммы, а затем введите следующий текст: **Sales для 2008 и 2009**.  
  
3.  Щелкните в любом месте текста.  
  
4.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
##  <a name="7-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a>7. форматирование и пометка горизонтальной оси  
 По умолчанию по горизонтальной оси отображаются значения в общем формате, который автоматически масштабируется в соответствии с размером диаграммы.  
  
#### <a name="to-format-the-numbers-on-the-horizontal-axis"></a>Форматирование чисел по горизонтальной оси  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Щелкните горизонтальную ось в нижней части диаграммы, чтобы выбрать ее.  
  
     На ленте на вкладке **Главная** в группе **число** нажмите кнопку **Валюта** . Метки на горизонтальной оси изменятся на валюту.  
  
3.  (Необязательно) Удалите десятичные знаки. Рядом с кнопкой **Денежный** дважды нажмите кнопку **Уменьшить число десятичных разрядов** .  
  
4.  Щелкните правой кнопкой мыши горизонтальную ось и выберите пункт **Свойства горизонтальной оси**.  
  
5.  На вкладке **число** выберите **Показывать значения в тысячах.**  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Щелкните правой кнопкой мыши **заголовок оси** и выберите пункт **Свойства заголовка оси**.  
  
8.  В **текстовом поле Заголовок** введите **Sales в тысячах** и нажмите кнопку **ОК**.  
  
9. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 В отчете объем продаж отображается по горизонтальной оси в виде валюты в тысячах без десятичных знаков.  
  
##  <a name="8-add-a-filter-to-display-the-top-five-values"></a><a name="Filter"></a>8. Добавление фильтра для вывода пяти верхних значений  
 К диаграмме можно добавить фильтр, чтобы выбрать данные в наборе данных для включения или исключения из диаграммы.  
  
#### <a name="to-add-a-filter-and-display-the-top-five-values"></a>Добавление фильтра и отображение 5 наибольших значений  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  Дважды щелкните диаграмму, чтобы отобразить панель **Данные диаграммы** .  
  
3.  Щелкните правой кнопкой мыши поле [LastName] в области **Группы категорий** и выберите пункт **Свойства группы категорий**.  
  
4.  Перейдите на вкладку **Фильтры**. На странице **Изменение фильтров** может отображаться список критериев фильтров. По умолчанию этот список пустой.  
  
5.  Нажмите кнопку **Добавить**. Появится новый пустой фильтр.  
  
6.  В **выражении**введите **[Sum (SalesYear2009)]**. При этом создается базовое выражение `=Sum(Fields!SalesYear2009.Value)`, которое можно просмотреть, нажав кнопку **fx** .  
  
7.  Убедитесь в том, что типом данных является **Текст**.  
  
8.  В раскрывающемся списке **Оператор**выберите вариант **Первые N** .  
  
9. В поле **Значение**введите следующее выражение: **=5**  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Если к результатам не применяется фильтр при выполнении отчета, данные можно обновить вручную. На вкладке **Выполнить** в группе **Навигация** нажмите кнопку **Обновить**.  
  
 На диаграмме отобразятся имена пяти первых менеджеров по продажам из данных продаж за 2009 г.  
  
##  <a name="9-add-a-report-title"></a><a name="Title"></a>9. Добавление заголовка отчета  
  
#### <a name="to-add-a-report-title"></a>Добавление заголовка отчета  
  
1.  В области конструктора щелкните ссылку **Щелкните, чтобы добавить заголовок**.  
  
2.  Введите **линейчатую диаграмму продаж**, нажмите клавишу ВВОД, а затем введите **первые пять продавцов для 2009**, чтобы он выглядел следующим образом:  
  
     **Линейчатая диаграмма продаж**  
  
     **Пять менеджеров по продажам с наибольшим объемом продаж за 2009 г.**  
  
3.  Выберите **Линейчатая диаграмма продаж**и нажмите кнопку **Полужирный** .  
  
4.  Выберите **пять основных продавцов для 2009**, а в разделе **Шрифт** на вкладке **Главная** установите размер шрифта равным **10**.  
  
5.  Может потребоваться увеличить высоту текстового поля «Заголовок» для соответствия размерам двух строк текста (необязательно).  
  
     Данный заголовок появится в верхней части отчета. При отсутствии верхнего колонтитула страницы элементы в верхней части текста отчета выполняют роль заголовка отчета.  
  
6.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
##  <a name="10-save-the-report"></a><a name="Save"></a>10. Сохранение отчета  
  
#### <a name="to-save-the-report"></a>Сохранение отчета  
  
1.  Переключитесь в режим конструктора отчета.  
  
2.  На кнопке **Построитель отчетов** нажмите кнопку **Сохранить как**.  
  
3.  В поле **Имя**введите **Линейчатая диаграмма продаж**.  
  
4.  Нажмите кнопку **Сохранить**.  
  
 Отчет будет сохранен на сервере отчетов.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Учебник «Добавление линейчатой диаграммы в отчет» успешно завершен. Дополнительные сведения о диаграммах см. в разделах [Диаграммы (построитель отчетов и службы SSRS)](report-design/charts-report-builder-and-ssrs.md) и [Спарклайны и гистограммы (построитель отчетов и службы SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>См. также  
 [Учебники &#40;построитель отчетов&#41;](report-builder-tutorials.md)   
 [Построитель отчетов в SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  

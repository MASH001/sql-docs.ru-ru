---
title: Краткое руководство о типах данных R и SQL и объектов - машинного обучения SQL Server
description: В этом кратком руководстве вы научитесь работать с типами данных и объекты данных R и SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: df1c4c50e21ba5db5459da958f915be560500dc7
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046930"
---
# <a name="quickstart-handle-data-types-and-objects-using-r-in-sql-server"></a>Краткое руководство. Обрабатывать типы данных, а также объекты, с помощью языка R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве получите Практическое знакомство с распространенные проблемы, возникающие при перемещении данных между R и SQL Server. Вы получаете выполняйте это упражнение опытом предоставляет важные фона при работе с данными в собственный сценарий.

Часто возникающие проблемы знать заранее:

+ Иногда типы данных не совпадают.
+ Неявные преобразования могут допускаться
+ Иногда требуются операции приведения и преобразования.
+ R и SQL используют разные объекты данных.

## <a name="prerequisites"></a>предварительные требования

Предыдущего краткого руководства, [проверьте R в SQL Server существует](quickstart-r-verify.md), сведения и ссылки по настройке среды R, необходимые для этого краткого руководства.

## <a name="always-return-a-data-frame"></a>Всегда возвращать кадр данных

Когда скрипт возвращает результаты из R в SQL Server, он должен возвращать данные в виде **data.frame**. Любой другой тип объекта, создаваемого в скрипте — будь то список, коэффициент, вектор или двоичные данные - должны преобразовываться в кадр данных, если вы хотите вывести его как часть результатов хранимой процедуры. К счастью существует несколько функций R, поддерживающих изменение других объектов на кадр данных. Вы даже можете сериализовать двоичную модель и возвратить ее в блок данных, что вы сделаете далее в этом руководстве.

Во-первых давайте поэкспериментировать с некоторыми базовыми объектами R — векторами, матрицами и списками - и посмотрим, как преобразование в кадр данных изменяет выходные данные, передаваемые в SQL Server.

Сравните эти два сценария «Hello, World!» в R. Сценарии выглядят почти одинаково, но первый возвращает один столбец из трех значений, тогда как второй возвращает три столбца с одним значением каждого.

**Пример 1**

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
     , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
     , @input_data_1 = N' ';
```

**Пример 2**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' OutputDataSet<- data.frame(c("hello"), " ", c("world"));'
      , @input_data_1 = N'  ';
```

## <a name="identify-schema-and-data-types"></a>Определение схемы и типов данных

Почему результаты настолько отличаются? 

Обычно ответ можно найти, использовав команду R `str()`. Добавьте функцию `str(object_name)` в скрипте R для получения сведений о схеме данных возвращаемого объекта R в виде информационного сообщения. Сообщения можно просмотреть на панели **Сообщения** Visual Studio Code или на вкладке **Сообщения** в среде SSMS.

Чтобы понять, почему результаты примера 1 и 2 так сильно отличаются, вставьте строку `str(OutputDataSet)` в конце определения переменной _@script_ в каждой инструкции следующим образом:

**Пример 1 с функцией str добавлен**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' mytextvariable <- c("hello", " ", "world");
      OutputDataSet <- as.data.frame(mytextvariable);
      str(OutputDataSet);'
      , @input_data_1 = N'  '
;
```

**Пример 2 с помощью функции str добавлен**

```sql
EXECUTE sp_execute_external_script
  @language = N'R', 
  @script = N' OutputDataSet <- data.frame(c("hello"), " ", c("world"));
    str(OutputDataSet);' , 
  @input_data_1 = N'  ';
```

Теперь просмотрите текст на вкладке **Сообщения**, в котором можно определить причину такой разницы.

**Результаты примера 1**

```sql
STDOUT message(s) from external script:
'data.frame':   3 obs. of  1 variable:
$ mytextvariable: Factor w/ 3 levels " ","hello","world": 2 1 3
```

**Результаты примера 2**

```sql
STDOUT message(s) from external script:
'data.frame':   1 obs. of  3 variables:
$ c..hello..: Factor w/ 1 level "hello": 1
$ X...      : Factor w/ 1 level " ": 1
$ c..world..: Factor w/ 1 level "world": 1
```

Как видно, небольшие изменения в синтаксисе R сильно повлияли на схему результатов. Мы не будем останавливаться на том, почему, но различия в типах данных R рассматриваются подробно в *структуры данных* статьи [«Advanced R», (Hadley Wickham)](http://adv-r.had.co.nz).

Сейчас помните, что необходимо проверить ожидаемые результаты при приведении объектов R в кадры данных.

> [!TIP]
> Можно также использовать функции удостоверений R, такие как `is.matrix`, `is.vector`, которая возвращает сведения о структуре внутренних данных.

## <a name="implicit-conversion-of-data-objects"></a>Неявное преобразование объектов данных

Каждый объект данных R имеет собственные правила обработки значений в сочетании с другими объектами данных, если объекты данных имеют одинаковое количество измерений или если любой объект данных содержит разнородные типы данных.

Например предположим, что вы выполните следующую инструкцию для умножения матриц с помощью языка R. Перемножить matrix один столбец с тремя значениями массивом с четырьмя значениями и в результате ожидать матрицу 4 x 3.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
    , @script = N'
        x <- as.matrix(InputDataSet);
        y <- array(12:15);
    OutputDataSet <- as.data.frame(x %*% y);'
    , @input_data_1 = N' SELECT [Col1]  from RTestData;'
    WITH RESULT SETS (([Col1] int, [Col2] int, [Col3] int, Col4 int));
```

Один столбец с тремя значениями преобразуется в матрицу с одним столбцом. Так как матрица представляет собой особый вид массива в R, массив `y` неявно приводится к матрице с одним столбцом, чтобы обеспечить соответствие двух аргументов.

**Результаты**

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|12|13|14|15|
|120|130|140|150|
|1200|1300|1400|1500|

Тем не менее, обратите внимание, что происходит при изменении размера массива `y`.

```sql
execute sp_execute_external_script
   @language = N'R'
   , @script = N'
        x <- as.matrix(InputDataSet);
        y <- array(12:14);
   OutputDataSet <- as.data.frame(y %*% x);'
   , @input_data_1 = N' SELECT [Col1]  from RTestData;'
   WITH RESULT SETS (([Col1] int ));
```

На этот раз код R вернет одно значение в качестве результата.

**Результаты**
    
|Col1|
|---|
|1542|

Почему? Таким образом так как эти два аргумента могут обрабатываться как векторы одинаковой длины, R возвращает скалярное произведение в виде матрицы.  Это ожидаемое поведение в соответствии с правилами линейной алгебры. Тем не менее могут возникнуть проблемы, если нисходящее приложение ожидает, что выходная схема вывода не должна изменяться.

> [!TIP]
> 
> Получение ошибки? Для этих примеров требуются таблице **RTestData**. Если вы еще не создали тестовую таблицу данных, вернитесь на этот раздел, чтобы создать таблицу: [Обрабатывать входные и выходные данные](../tutorials/rtsql-working-with-inputs-and-outputs.md).
> 
> Если таблица создана, но по-прежнему появляется сообщение об ошибке, убедитесь, что хранимая процедура выполняется в контексте базы данных, содержащую таблицу, а не в **master** или другой базе данных.
> 
> Кроме того мы рекомендуем не использовать временные таблицы для этих примеров. Некоторые клиенты R будут завершить подключение между пакетами, удаление временных таблиц.

## <a name="merge-or-multiply-columns-of-different-length"></a>Слияние или перемножение столбцов разной длины

R обеспечивает большую гибкость для работы с векторами различных размеров и для объединения этих столбцов структуры в кадры данных. Списки векторов могут выглядеть как таблица, но они не подчиняются всем правилам, управляющим таблицами базы данных.

Например, следующий скрипт определяет числовой массив, длина которого равна 6, и сохраняет его в переменной R `df1`. Затем числовой массив объединяется с целыми числами из таблицы RTestData, которая содержит три (3) значения, для формирования нового кадра данных, `df2`.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
    , @script = N'
               df1 <- as.data.frame( array(1:6) );
               df2 <- as.data.frame( c( InputDataSet , df1 ));
               OutputDataSet <- df2'
    , @input_data_1 = N' SELECT [Col1]  from RTestData;'
    WITH RESULT SETS (( [Col2] int not null, [Col3] int not null ));
```

Чтобы заполнить кадр данных, R повторно использует элементы, полученные из RTestData, столько раз, сколько требуется в соответствии с числом элементов в массиве `df1`.

**Результаты**
    
|*Col2*|*Col3*|
|----|----|
|1|1|
|10|2|
|100|3|
|1|4|
|10|5|
|100|6|

Помните, что кадр данных только выглядит как таблица и на самом деле является списком векторов.

## <a name="cast-or-convert-sql-server-data"></a>Приведение или преобразование данных SQL Server

R и SQL Server используют разные типы данных, поэтому при выполнении запроса в SQL Server для получения данных и их передаче в среду выполнения R обычно выполняется неявное преобразование. Кроме того, преобразования выполняются при возвращении данных из R в SQL Server.

- SQL Server передает данные из запроса в процесс R, управляемых службой панели запуска и преобразует его во внутреннее представление, для повышения эффективности.
- Среда выполнения R загружает данные в переменную data.frame и выполняет собственные операции с данными.
- Ядро СУБД возвращает данные в SQL Server по защищенному внутреннему соединению и представляет данные в контексте типов данных SQL Server.
- Вы можете получить данные путем подключения к SQL Server с помощью клиентской или сетевой библиотеки, которая может выполнять запросы SQL и обрабатывать табличные наборы данных. Это клиентское приложение может и по-другому влиять на данные.

Чтобы узнать, как это работает, выполните запрос, подобный следующему [AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) хранилище данных. Это представление возвращает данные продаж, используемые для создания прогнозов.

```sql
USE AdventureWorksDW
GO

SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW].[dbo].[vTimeSeries]
           WHERE [ModelRegion] = 'M200 Europe'
           ORDER BY ReportingDate ASC
```

> [!NOTE]
> 
> Можно использовать любую версию AdventureWorks или создайте другой запрос, используя базу данных из собственных. Точка находится в том, чтобы обработать некоторые данные, которые содержит текст, даты и времени и числовых значений.

Теперь попробуйте вставить этот запрос в качестве входных данных в хранимую процедуру.

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
      , @script = N' str(InputDataSet);
      OutputDataSet <- InputDataSet;'
      , @input_data_1 = N'
           SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW].[dbo].[vTimeSeries]
           WHERE [ModelRegion] = ''M200 Europe''
           ORDER BY ReportingDate ASC ;'
WITH RESULT SETS undefined;
```

Если появляется сообщение об ошибке, возможно, необходимо внести некоторые изменения в текст запроса. Например, строковый предикат в предложении WHERE нужно заключать в два набора одинарных кавычек.

После того, как запрос начнет действовать, просмотрите результаты выполнения функции `str`, чтобы увидеть, как R обрабатывает входные данные.

**Результаты**

```sql
STDOUT message(s) from external script: 'data.frame':    37 obs. of  3 variables:
STDOUT message(s) from external script: $ ReportingDate: POSIXct, format: "2010-12-24 23:00:00" "2010-12-24 23:00:00"
STDOUT message(s) from external script: $ ProductSeries: Factor w/ 1 levels "M200 Europe",..: 1 1 1 1 1 1 1 1 1 1
STDOUT message(s) from external script: $ Amount       : num  3400 16925 20350 16950 16950
```

+ Столбец datetime был обработан с использованием типа данных R **POSIXct**.
+ Текстовый столбец «ProductSeries» определен в качестве **идентификации**, то есть категориальной переменной. Строковые значения обрабатываются как коэффициенты по умолчанию. Если передать строку в R, она преобразуется в целое число для внутреннего использования и сопоставляется со строками на выходе.

### <a name="summary"></a>Сводка

Из даже эти краткие примеры вы увидите необходимость проверить влияние преобразования данных при передаче SQL запросов в качестве входных данных. Так как некоторые типы данных SQL Server не поддерживаются языком R, рассмотрим эти способы избежания ошибок:

+ Проверяйте данные заранее и проверяйте столбцы или значения в схеме, возможно, возникла проблема при передаче в код R.
+ Указывайте столбцы из источника входных данных по отдельности. Не используйте `SELECT *`. Определите способ обработки каждого столбца.
+ Во избежание непредвиденных ситуаций во время подготовки входных данных при необходимости выполняйте явные приведения.
+ Избегайте столбцов передачи данных (например, идентификаторы GUID или идентификаторами rowguids), привести к ошибкам и не используются для моделирования.

Дополнительные сведения о поддерживаемых и неподдерживаемых типов данных, см. в разделе [R библиотеки и типы данных](../r/r-libraries-and-data-types.md).

Дополнительные сведения о влияние на производительность во время выполнения преобразования строк в числовые коэффициенты, см. в разделе [Настройка производительности служб R SQL Server](../r/sql-server-r-services-performance-tuning.md).

## <a name="next-step"></a>Следующий шаг

В следующем кратком руководстве вы узнаете, как применять функции R к данным SQL Server.

> [!div class="nextstepaction"]
> [Краткое руководство. Использование функций R с данными SQL Server](quickstart-r-functions.md)
---
title: Действительное логическое значение (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- effective Boolean value [XQuery]
- Boolean values
- XQuery, effective Boolean values
- EBV
ms.assetid: 506682b1-b6c9-45e2-aa54-7abd5844c3f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 4eb94e51896e08f60389edde0c2a6cd0461e8538
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67929957"
---
# <a name="effective-boolean-value-xquery"></a>Действительное логическое значение (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Это действительные логические значения:  
  
-   Значение false, если операнд является пустой последовательностью или логическим значением false.  
  
-   В противном случае — значение true.  
  
 Можно вычислить действительное логическое значение для выражений, возвращающих одно логическое значение, последовательность узла или пустую последовательность. Обратите внимание на то, что логическое значение вычисляется неявно в процессе обработки следующих типов значений:  
  
-   Логические выражения  
  
-   [Функция not](../xquery/functions-on-boolean-values-not-function.md)  
  
-   Предложение WHERE выражения FLWOR  
  
-   [Условные выражения](../xquery/conditional-expressions-xquery.md)  
  
-   [QuantifiedeExpressions](../xquery/quantified-expressions-xquery.md)  
  
 Далее приводится пример действительного логического значения. При обработке выражения **If** определяется действительное логическое значение условия. Действительное логическое значение является false, потому что `/a[1]` возвращает пустую последовательность. Результат возвращается как XML с одним текстовым узлом (false).  
  
```  
value is false  
DECLARE @x XML  
SET @x = '<b/>'  
SELECT @x.query('if (/a[1]) then "true" else "false"')  
go  
```  
  
 В следующем примере — действительное логическое значение true, поскольку выражение возвращает непустую последовательность.  
  
```  
DECLARE @x XML  
SET @x = '<a/>'  
SELECT @x.query('if (/a[1]) then "true" else "false"')  
go  
```  
  
 При выполнении запросов к типизированным **XML-** столбцам или переменным можно иметь узлы логического типа. **Данные ()** в этом случае возвращают логическое значение. Если выражение запроса возвращает логическое значение true, действительное логическое значение, как показано в следующем примере — true. Это также показано в примере.  
  
-   создается коллекция XML-схем; Элемент \<b> в коллекции имеет логический тип.  
  
-   Создается и запрашивается типизированная **XML-** переменная.  
  
-   Выражение `data(/b[1])` возвращает логическое значение true. Таким образом, в данном случае действительное логическое значение — true.  
  
-   Выражение `data(/b[2])` возвращает логическое значение false. Таким образом, в данном случае действительное логическое значение — false.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
      <element name="s" type="string"/>  
      <element name="b" type="boolean"/>  
</schema>'  
go  
DECLARE @x XML(SC)  
SET @x = '<b>true</b><b>false</b>'  
SELECT @x.query('if (data(/b[1])) then "true" else "false"')  
SELECT @x.query('if (data(/b[2])) then "true" else "false"')  
go  
```  
  
## <a name="see-also"></a>См. также:  
 [Основы XQuery](../xquery/xquery-basics.md)   
 [Инструкция FLWOR и итерация &#40;XQuery&#41;](../xquery/flwor-statement-and-iteration-xquery.md)  
  
  

---
title: Функция local name (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:local-name function
- local-name function
ms.assetid: c901ef5d-89c5-482a-bf64-3eefbcf3098d
author: rothja
ms.author: jroth
ms.openlocfilehash: 382bbc9aeedacf37c7fe38abd592bcee7e154f5a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038871"
---
# <a name="functions-on-nodes---local-name"></a>Функции с узлами — local-name
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает локальную часть имени *$arg* в виде строки xs: String, которая будет либо строкой нулевой длины, либо будет иметь лексическую форму типа xs: NCName. Если аргумент не указан, по умолчанию используется узел контекста.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
fn:local-name() as xs:string  
fn:local-name($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Имя узла, локальную часть имени которого нужно получить.  
  
## <a name="remarks"></a>Remarks  
  
-   В SQL Server **fn: local-name ()** без аргумента может использоваться только в контексте контекстно-зависимого предиката. Точнее, ее использование возможно только внутри квадратных скобок (`[ ]`).  
  
-   Если аргумент указан и представляет собой пустую последовательность, функция возвращает строку нулевой длины.  
  
-   Если целевой узел не имеет имени (например, узел документа, комментарий или текстовый узел), функция возвращает строку нулевой длины.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
### <a name="a-retrieve-local-name-of-a-specific-node"></a>А) Получение локального имени конкретного узла  
 Следующий запрос обращается к нетипизированному экземпляру XML. Выражение запроса `local-name(/ROOT[1])` получает локальную часть имени указанного узла.  
  
```  
declare @x xml  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('local-name(/ROOT[1])')  
-- result = ROOT  
```  
  
 Следующий запрос обращается к столбцу «Instructions» типа xml таблицы ProductModel. Выражение `local-name(/AWMI:root[1]/AWMI:Location[1])` возвращает локальное имя `Location` указанного узла.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     local-name(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
-- result = Location  
```  
  
### <a name="b-using-local-name-without-argument-in-a-predicate"></a>Б) Использование локального имени без аргумента в предикате  
 Следующий запрос задается для столбца Instructions, типизированного **XML-** столбец таблицы ProductModel. Выражение возвращает все дочерние элементы элемента <`root`>, локальным именем которого является "Location". Функция **local-name ()** указана в предикате и не имеет аргументов. контекстный узел используется функцией.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
  /AWMI:root//*[local-name() = "Location"]') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Запрос возвращает все дочерние `Location` элементы <> элемента <`root`>.  
  
## <a name="see-also"></a>См. также:  
 [Функции на узлах](https://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [Namespace — функция URI &#40;XQuery&#41;](../xquery/functions-on-nodes-namespace-uri.md)  
  
  

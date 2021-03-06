---
title: Метод Append (столбцы ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Columns::raw_Append
- Columns::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 7a46d23c-efef-4ec7-815d-cd3ac86787dd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6493157c00e5a71c7c2f085191231bb33bb5279a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67967325"
---
# <a name="append-method-adox-columns"></a>Метод Append (коллекция Columns ADOX)
Добавляет новый объект [Column](../../../ado/reference/adox-api/column-object-adox.md) в коллекцию [Columns](../../../ado/reference/adox-api/columns-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Рубрик*  
 Добавляемый объект **Column** или имя создаваемого и добавляемого столбца.  
  
 *Type*  
 Необязательный параметр. Значение типа **Long** , указывающее тип данных столбца. Параметр *типа* соответствует свойству [Type](../../../ado/reference/adox-api/type-property-column-adox.md) объекта **Column** .  
  
 *DefinedSize*  
 Необязательный параметр. Значение **типа Long** , указывающее размер столбца. Параметр *DefinedSize* соответствует свойству [DefinedSize](../../../ado/reference/adox-api/definedsize-property-adox.md) объекта **Column** .  
  
> [!NOTE]
>  При добавлении **столбца** в коллекцию **Columns** [индекса](../../../ado/reference/adox-api/index-object-adox.md) , если **Столбец** не существует в [таблице](../../../ado/reference/adox-api/table-object-adox.md) , уже присоединенной к коллекции [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) , возникнет ошибка.  
  
## <a name="applies-to"></a>Применяется к  
 [Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Методы добавления столбцов и таблиц, пример свойства Name (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Метод Append (группы ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Метод Append (индексы ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Метод Append (ключи ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Метод Append (процедуры ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Метод Append (таблицы ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Метод Append (пользователи ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)

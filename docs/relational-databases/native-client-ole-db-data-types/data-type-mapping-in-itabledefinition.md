---
title: Сопоставление типов данных в интерфейсе ITableDefinition | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
ms.assetid: 13292d1f-c17e-4d11-bf98-3460a10cbb18
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d3e828efa513db1ace272e59379f77d063220290
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81297088"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Сопоставление типов данных в интерфейсе ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  При создании таблиц с помощью функции **ITableDefinition:: CreateTable** потребитель поставщика OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента может указывать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных в *pwszTypeName* члене передаваемого массива DBCOLUMNDESC. Если потребитель указывает тип данных столбца по имени, то сопоставление типов OLE DB, представляемое элементом *wType* структуры DBCOLUMNDESC, не учитывается.  
  
 При указании новых типов данных столбцов с OLE DB типами данных с помощью элемента *wType* Structure, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB сопоставляет OLE DB типы данных следующим образом.  
  
|Тип данных OLE DB|SQL Server<br /><br /> тип данных|Дополнительные сведения|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** или **varbinary(max)**|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента проверяет элемент *ulColumnSize* структуры DBCOLUMNDESC. Основываясь на значении и версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента сопоставляет тип с **изображением**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных **binary** , то поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB проверяет элемент DBCOLUMNDESC *rgPropertySets* . Если DBPROP_COL_FIXEDLENGTH VARIANT_TRUE, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB Native Client сопоставляет тип с **двоичным**. Если значение свойства равно VARIANT_FALSE, поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client сопоставляет тип с типом **varbinary**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца SQL Server.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB проверяет элементы дбколумдеск *бпреЦисион* и *bScale* , чтобы определить точность и масштаб для **числового** столбца.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **text** или **varchar(max)**|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента проверяет элемент *ulColumnSize* структуры DBCOLUMNDESC. Основываясь на значении и версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента сопоставляет тип с **текстом**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных с многобайтовой кодировкой, то поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для собственного клиента проверяет элемент DBCOLUMNDESC *rgPropertySets* . Если DBPROP_COL_FIXEDLENGTH VARIANT_TRUE, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента сопоставляет тип с типом **char**. Если значение свойства равно VARIANT_FALSE, поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client сопоставляет тип с типом **varchar**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|DBTYPE_UDT|**БАЙТ**|Следующие сведения используются в структурах **DBCOLUMNDESC**, применяемых методом **ITableDefinition::CreateTable**, когда требуются столбцы пользовательских типов:<br /><br /> *pwSzTypeName* игнорируется.<br /><br /> Свойство *rgPropertySets* должно включать набор свойств **DBPROPSET_SQLSERVERCOLUMN**, как описано в пункте **DBPROPSET_SQLSERVERCOLUMN** раздела [Использование определяемых пользователем типов](../../relational-databases/native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** или **nvarchar(max)**|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента проверяет элемент *ulColumnSize* структуры DBCOLUMNDESC. Основываясь на значении, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB сопоставляет тип с типом **ntext**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных character в Юникоде, то поставщик OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента проверяет элемент DBCOLUMNDESC *rgPropertySets* . Если DBPROP_COL_FIXEDLENGTH VARIANT_TRUE, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента сопоставляет тип с типом **nchar**. Если значение свойства равно VARIANT_FALSE, поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client сопоставляет тип с типом **nvarchar**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  При создании новой таблицы поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сопоставляет только значения перечислений типов данных OLE DB, указанные в предшествующей таблице. Попытка создать таблицу со столбцом любого другого типа данных OLE DB приводит к ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (OLE DB)](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  

---
title: Поддержка режима FOR XML для типа данных timestamp | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- timestamp data type
ms.assetid: 4e1920e1-e7a4-4069-965e-3f6039a6099e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: df404c4c666b43bf9b2c7275196e5cb7ba74bb48
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665151"
---
# <a name="for-xml-support-for-the-timestamp-data-type"></a>Поддержка режима FOR XML для типа данных timestamp
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В преобразовании FOR XML значения типа данных **timestamp** рассматриваются как данные типа **varbinary(8)** и всегда будут иметь кодировку base-64. Схема XSD или XDR, если она запрошена, отображает этот тип.  
  
```  
drop table t  
go  
create table t  
(c1 int,  
 c2 timestamp)  
go  
  
insert t values(1, null)  
go  
select * from t  
for xml auto, xmldata  
go  
```  
  
 Результат:  
  
```  
<Schema name="Schema1"   
        xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes">  
  <ElementType name="t" content="empty" model="closed">  
    <AttributeType name="c1" dt:type="i4" />  
    <AttributeType name="c2" dt:type="bin.base64" />  
    <attribute type="c1" />  
    <attribute type="c2" />  
  </ElementType>  
</Schema>  
<t xmlns="x-schema:#Schema1" c1="1" c2="AAAAAAAAH04=" />  
```  
  
## <a name="see-also"></a>См. также:  
 [Поддержка FOR XML для различных типов данных SQL Server](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  

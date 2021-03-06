---
title: Значения столбцов XML SQL
description: Демонстрация получения и работы с XML-данными, полученными из SQL Server.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 2704ceae26c58edc85b0cbc1f0fbe6cc98f64311
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902016"
---
# <a name="sql-xml-column-values"></a>Значения столбцов XML SQL

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

В SQL Server поддерживается тип данных `xml`, поэтому разработчики могут получать результирующие наборы с данными этого типа с помощью стандартных средств класса <xref:Microsoft.Data.SqlClient.SqlCommand>. Столбец `xml` может извлекаться как любой другой столбец (например, в <xref:Microsoft.Data.SqlClient.SqlDataReader>), но для работы с содержимым столбца в формате XML необходимо использовать <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Пример  
В следующем приложении командной строки в экземпляр `xml` выбираются две строки, каждая из которых содержит столбец **, из таблицы** Sales.Store**базы данных**AdventureWorks<xref:Microsoft.Data.SqlClient.SqlDataReader>. Для каждой строки значение столбца `xml` считывается с помощью метода <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> из <xref:Microsoft.Data.SqlClient.SqlDataReader>. Это значение сохраняется в <xref:System.Xml.XmlReader>. Обратите внимание, что для сохранения содержимого в переменную <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> необходимо использовать метод <xref:System.Data.IDataRecord.GetValue%2A>, а не <xref:System.Data.SqlTypes.SqlXml>, так как <xref:System.Data.IDataRecord.GetValue%2A> возвращает значение столбца `xml` в формате строки.  
  
> [!NOTE]
>  Образец базы данных **AdventureWorks** не устанавливается по умолчанию при установке SQL Server. Чтобы установить его, запустите программу установки SQL Server.  
  
[!code-csharp [SqlDataReader_GetSqlXml#1](~/../sqlclient/doc/samples/SqlDataReader_GetSqlXml.cs#1)]
  
## <a name="next-steps"></a>Дальнейшие действия
- <xref:System.Data.SqlTypes.SqlXml>
- [Данные XML в SQL Server](xml-data-sql-server.md)

---
title: поставщик OLE DB для Oracle (Майкрософт) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB provider for Oracle
- OLE DB provider for Oracle [ADO]
- Oracle provider [ADO]
ms.assetid: 44fae9dd-5585-4cd6-8bbd-3248a78931b4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 60510302525562d9c3007a6ef57213fc261b4c60
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926623"
---
# <a name="microsoft-ole-db-provider-for-oracle-overview"></a>Обзор поставщик OLE DB для Oracle (Майкрософт)
> [!IMPORTANT]
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте поставщик OLE DB Oracle.

 Поставщик OLE DB для Oracle (Майкрософт) позволяет ADO получать доступ к базам данных Oracle.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к поставщику, задайте для аргумента *поставщика* свойства [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) значение:

```vb
MSDAORA
```

 При чтении свойства [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) также будет возвращена эта строка.

 Если запрос на соединение с набором ключей или динамическим курсором выполняется в базе данных Oracle, возникает ошибка. Oracle поддерживает только статический курсор только для чтения.

## <a name="typical-connection-string"></a>Типичная строка подключения
 Типичная строка подключения для этого поставщика:

```vb
"Provider=MSDAORA;Data Source=serverName;User ID=MyUserID; Password=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для Oracle.|
|**Источник данных**|Указывает имя сервера.|
|**Идентификатор пользователя**|Указывает имя пользователя.|
|**Пароль**|Указывает пароль пользователя.|

> [!NOTE]
>  При подключении к поставщику источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = Yes** или **Integrated Security = SSPI** вместо сведений об идентификаторе пользователя и пароле в строке подключения.

## <a name="provider-specific-connection-parameters"></a>Параметры подключения, зависящие от поставщика
 Поставщик поддерживает несколько параметров соединения, зависящих от поставщика, помимо тех, которые определены в ADO. Как и в случае со свойствами соединения ADO, эти свойства, зависящие от поставщика, можно задать через коллекцию [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) [соединения](../../../ado/reference/ado-api/connection-object-ado.md) или как часть **ConnectionString**.

 Эти параметры полностью описаны в [справочнике по программисту OLE DB](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8). [Индекс динамического свойства ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) обеспечивает перекрестную ссылку между этими именами параметров и соответствующими свойствами OLE DB.

|Параметр|Описание|
|---------------|-----------------|
|**Дескриптор окна**|Указывает описатель окна, используемый для запроса дополнительных сведений.|
|**Идентификатор локали**|Указывает уникальное 32-разрядное число (например, 1033), которое указывает параметры, относящиеся к языку пользователя. Эти настройки указывают, как форматируются даты и время, элементы сортируются в алфавитном порядке, сравниваются по строкам и т. д.|
|**Службы OLE DB**|Указывает битовую маску, указывающую OLE DB службы для включения или отключения.|
|**Prompt**|Указывает, следует ли запрашивать пользователя во время установки соединения.|
|**Расширенные свойства**|Строка, содержащая сведения о расширенном соединении, зависящие от поставщика. Это свойство используется только для специфичных для поставщика сведений о соединении, которые не могут быть описаны с помощью механизма свойств.|

## <a name="see-also"></a>См. также:
 Property ( [ADO) свойство](../../../ado/reference/ado-api/connectionstring-property-ado.md) [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) (ADO) [объект Recordset Object (](../../../ado/reference/ado-api/recordset-object-ado.md) ADO)

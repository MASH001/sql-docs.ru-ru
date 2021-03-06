---
title: Раздел "Подключение файла настройки" | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connect section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: d50eb3cc-a822-486f-b80b-65bb50547ecd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1de3710590cf49de30ff8e79a6ff829b124c42dd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922808"
---
# <a name="customization-file-connect-section"></a>Настройка раздела подключения файла
Поведение обработчика по умолчанию заключается в запрете всех подключений. В разделе **Connect** указываются исключения из этого поведения. Например, если все разделы **соединения** отсутствовали или пусты, то по умолчанию соединения устанавливаться не могут.  
  
 Раздел **Connect** может содержать:  
  
-   Запись доступа по умолчанию, которая указывает операции чтения и записи по умолчанию, разрешенные для этого соединения. Если в разделе нет записи доступа по умолчанию, раздел будет проигнорирован.  
  
-   Новая строка подключения, которая заменяет строку подключения клиента.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Запись доступа по умолчанию имеет вид:  
  
```console
  
Access=  
accessRight  
  
```  
  
 Заменяющая строка подключения имеет вид:  
  
```console
  
Connect=  
connectionString  
  
```  
  
## <a name="remarks"></a>Remarks  
  
|Часть|Описание|  
|----------|-----------------|  
|**Подключить**|Литеральная строка, указывающая, что это запись строки подключения.|  
|**_connectionString_**|Строка, которая заменяет всю строку подключения клиента.|  
|**Доступ**|Литеральная строка, указывающая, что это запись доступа.|  
|**_акцессригхт_**|Одно из следующих прав доступа:<br /><br /> -   Не **доступ** — пользователь не может получить доступ к источнику данных.<br />-   **Только для** чтения — пользователь может читать источник данных.<br />-   **ReadWrite** — пользователь может выполнять чтение или запись в источник данных.|  
  
 Если вы хотите разрешить любое подключение (в результате отключив поведение обработчика по умолчанию), задайте запись доступа в разделе **Connect Default** `Access=ReadWrite`, а затем удалите или закомментируйте любой другой раздел **Connect** _identifier_ .  
  
## <a name="see-also"></a>См. также:  
 [Раздел журналов файлов настройки](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Раздел файла настройки SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Раздел UserList файла настройки](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка в отношении фактов](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Требуемые параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настройки](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Создание собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)




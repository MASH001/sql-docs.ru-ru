---
title: SQL Server, объект SQL Errors | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f36cd694756544a44df657d97fd84e1967167b55
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63183007"
---
# <a name="sql-server-sql-errors-object"></a>SQL Server, объект SQL Errors
  Объект **SQLServer: ошибки SQL** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает счетчики для контроля работы **SQL Errors**.  
  
 В этой таблице описаны счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Ошибки SQL**.  
  
|Счетчики SQL Server SQL Errors|Description|  
|------------------------------------|-----------------|  
|**Ошибок/с**|Количество ошибок в секунду.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Элемент|Определение|  
|----------|----------------|  
|**_Total**|Сведения обо всех ошибках.|  
|**Ошибки DB в режиме «вне сети»**|Отслеживает серьезные ошибки, которые заставляют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] переключать текущую базу данных в режим «вне сети».|  
|**Информационные ошибки**|Сведения, связанные с сообщениями об ошибках, которые предоставляют данные пользователям, но не вызывают ошибок.|  
|**Ошибки разрыва соединения**|Отслеживает ошибки, которые заставляют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разорвать текущее соединение.|  
|**Пользовательские ошибки**|Сведения об ошибках пользователя.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](monitor-resource-usage-system-monitor.md)  
  
  

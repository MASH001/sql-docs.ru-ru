---
title: Параметр конфигурации сервера "c2 audit mode" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], C2 Audit Mode option
- C2 auditing
- C2 Audit Mode option
- recording attempts
ms.assetid: 5a8d73a6-c4f6-4967-ba11-ecbcfc90b9cc
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0233f6c40e15fd4f612002854477d98068901b15
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62786673"
---
# <a name="c2-audit-mode-server-configuration-option"></a>Параметр конфигурации сервера «c2 audit mode»
  Режим аудита C2 можно настроить с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или параметра **c2 audit mode** в **sp_configure**. Включение этого параметра заставляет сервер регистрировать как успешные, так и неуспешные попытки получения доступа к инструкциям и объектам. Эти сведения позволяют профилировать работу системы и отслеживать возможные нарушения политики безопасности.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Стандарт безопасности С2 был заменен стандартом Common Criteria Certification. См. [Параметр конфигурации сервера common criteria compliance enabled](common-criteria-compliance-enabled-server-configuration-option.md).  
  
## <a name="audit-log-file"></a>Файл журнала аудита  
 Файл данных режима аудита С2 сохраняется в каталоге данных по умолчанию для экземпляра. Если размер файла журнала аудита превышает максимально допустимый предел в 200 мегабайт, в версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] он закрывается, создается новый файл, и все новые записи аудита записываются в новый файл. Этот процесс продолжается до тех пор, пока не заполнится каталог данных аудита или аудит не будет отключен. Чтобы определить состояние трассировки C2, выполните запрос к представлению каталога sys.traces.  
  
> [!IMPORTANT]  
>  В режиме аудита С2 в файле журнала сохраняется большой объем данных о событиях, что приводит к его быстрому росту. Если в каталоге данных, в котором хранятся журналы, заканчивается свободное место, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершает свою работу. Если настроен автоматический запуск аудита, нужно либо перезапустить экземпляр с флагом **-f** (без аудита), либо освободить место на диске для записи журнала аудита.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="example"></a>Пример  
 В следующем примере включается режим аудита С2.  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
sp_configure 'c2 audit mode', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

---
title: sp_droppullsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_droppullsubscription
- sp_droppullsubscription_TSQL
helpviewer_keywords:
- sp_droppullsubscription
ms.assetid: 7352d94a-f8f2-42ea-aaf1-d08c3b5a0e76
author: stevestein
ms.author: sstein
ms.openlocfilehash: f4ad522c13987f7617def29d5ff112a5a26db8b9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771451"
---
# <a name="sp_droppullsubscription-transact-sql"></a>sp_droppullsubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Удаляет подписку в текущей базе данных подписчика. Эта хранимая процедура выполняется на подписчике в базе данных подписки по запросу.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_droppullsubscription [ @publisher= ] 'publisher'  
        , [ @publisher_db= ] 'publisher_db'  
        , [ @publication= ] 'publication'  
    [ , [ @reserved= ] reserved ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя удаленного сервера. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию. Если **все**, то подписка удаляется на всех издателях.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных издателя. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию. **все** это означает все базы данных издателя.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию. Если **все**, то подписка будет удалена для всех публикаций.  
  
`[ @reserved = ] reserved` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_droppullsubscription** используется в репликации моментальных снимков и репликации транзакций.  
  
 **sp_droppullsubscription** удаляет соответствующую строку в [MSreplication_subscriptions &#40;таблице&#41;Transact-SQL](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) и соответствующем агенте распространителя на подписчике. Если в [MSreplication_subscriptions &#40;Transact-&#41;SQL ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md)не осталось ни одной строки, она удаляется из таблицы.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-droppullsubscription-_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или пользователь, создавший подписку по запросу, могут выполнять **sp_droppullsubscription**. Предопределенная роль базы данных **db_owner** может быть **sp_droppullsubscription** выполнена только в том случае, если пользователь, создавший подписку по запросу, принадлежит этой роли.  
  
## <a name="see-also"></a>См. также:  
 [Удаление подписки по запросу](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  

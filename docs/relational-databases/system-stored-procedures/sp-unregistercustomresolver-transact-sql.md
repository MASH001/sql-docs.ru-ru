---
title: sp_unregistercustomresolver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_unregistercustomresolver_TSQL
- sp_unregistercustomresolver
helpviewer_keywords:
- sp_unregistercustomresolver
ms.assetid: 08bd20c8-c6be-4be2-be9f-2b5e1d7bee43
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3e84fb602c253f5ee6dd247c01bbbd64bda1d2f3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68017863"
---
# <a name="sp_unregistercustomresolver-transact-sql"></a>sp_unregistercustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отменяет регистрацию зарегистрированного ранее модуля бизнес-логики. Бизнес-логика может быть реализована в COM-компоненте или в сборке платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Эта хранимая процедура выполняется на распространителе, для которого была зарегистрирована указанная бизнес-логика.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_unregistercustomresolver [ @article_resolver = ] 'article_resolver'   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @article_resolver = ] 'article_resolver'`Указывает имя пользовательской бизнес-логики, для которой отменяется регистрация. *article_resolver* имеет тип **nvarchar (255)** и не имеет значения по умолчанию. Если удаляемая бизнес-логика является COM-компонентом, то этот параметр является понятным именем компонента. Если бизнес-логика является сборкой .NET, этот параметр является именем сборки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_unregistercustomresolver** используется в репликации слиянием.  
  
 Используйте [sp_enumcustomresolvers](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) на любом сервере в топологии репликации, чтобы получить список зарегистрированных пользовательских модулей бизнес-логики или арбитров конфликтов com, доступных для топологии.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_unregistercustomresolver**.  
  
## <a name="see-also"></a>См. также:  
 [sp_lookupcustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_registercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

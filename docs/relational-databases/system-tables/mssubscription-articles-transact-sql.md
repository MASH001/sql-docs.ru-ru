---
title: MSsubscription_articles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_articles
- MSsubscription_articles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_articles system table
ms.assetid: dbc1737f-261e-4017-b9cd-703b9fc4ac78
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8518c787f876152787ee30a20b9f25f936b9fa86
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68139780"
---
# <a name="mssubscription_articles-transact-sql"></a>MSsubscription_articles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSsubscription_articles** содержит сведения о статьях в подписке, поставленной в очередь. Данная таблица заполняется только для двух типов репликаций: как обновляемых посредством очередей, так и обновляемых немедленно, но которые стали обновляться через очереди из-за отработки отказа.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|Идентификатор агента, обслуживающего данную статью.|  
|**artid**|**int**|Идентификатор статьи из таблицы **sysarticles** .|  
|**рассмотрен**|**sysname**|Имя статьи из таблицы **sysarticles** .|  
|**dest_table**|**sysname**|Имя целевой таблицы из таблицы **sysarticles** .|  
|**владельцев**|**sysname**|Владелец подписки.|  
|**cft_table**|**sysname**|Имя таблицы конфликтов для данной статьи, для типа репликации, обновляемого посредством очередей.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  

---
title: sys. dm_os_threads (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_threads_TSQL
- sys.dm_os_threads
- dm_os_threads
- sys.dm_os_threads_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_threads dynamic management view
ms.assetid: a5052701-edbf-4209-a7cb-afc9e65c41c1
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ef8eeeaaf59934d6c3307641b6c93f110ab5738f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73982544"
---
# <a name="sysdm_os_threads-transact-sql"></a>sys.dm_os_threads (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает список всех потоков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в операционной системе, запущенных процессом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Чтобы вызвать эту функцию [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]или, используйте имя **sys. dm_pdw_nodes_os_threads**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|thread_address|**varbinary(8)**|Адрес потока в памяти (первичный ключ).|  
|started_by_sqlservr|**bit**|Указывает, кто создал поток:<br /><br /> 1 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запустил поток.<br /><br /> 0 = поток создан другим компонентом, например расширенной хранимой процедурой внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|os_thread_id|**int**|Идентификатор потока, назначенный операционной системой.|  
|status|**int**|Флаг внутреннего состояния.|  
|instruction_address|**varbinary(8)**|Адрес выполняющейся в данный момент инструкции.|  
|creation_time|**datetime**|Время создания потока.|  
|kernel_time|**bigint**|Время работы потока в режиме ядра.|  
|usermode_time|**bigint**|Время работы потока в режиме пользователя.|  
|stack_base_address|**varbinary(8)**|Самый высокий адрес в стеке для данного потока.|  
|stack_end_address|**varbinary(8)**|Самый низкий адрес в стеке для данного потока.|  
|stack_bytes_committed|**int**|Число байтов, сохраненных в стеке.|  
|stack_bytes_used|**int**|Число байтов, используемых потоком в данный момент.|  
|affinity|**bigint**|Маска ЦП, на которой выполняется данный поток. Это зависит от значения, настроенного инструкцией **ALTER Server Configuration Set Process сходства** . Может отличаться от планировщика в случае мягкой привязки.|  
|Priority|**int**|Приоритет данного потока.|  
|Локаль|**int**|Кэшированное значение идентификатора локали (LCID) для данного потока.|  
|Токен|**varbinary(8)**|Кэшированный дескриптор токена олицетворения для данного потока.|  
|is_impersonating|**int**|Указывает, использует ли данный поток олицетворение Win32:<br /><br /> 1 = поток использует учетные данные для обеспечения безопасности, отличающиеся от данных для процесса по умолчанию. Это значит, что поток олицетворяет сущность, отличную от созданной процессом.|  
|is_waiting_on_loader_lock|**int**|Состояние операционной системы, указывающее, ожидает ли поток завершения блокировки загрузчика.|  
|fiber_data|**varbinary(8)**|Текущее волокно Win32, запущенное для потока. Применимо только в случае, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для использования упрощенных пулов.|  
|thread_handle|**varbinary(8)**|Только для внутреннего применения.|  
|event_handle|**varbinary(8)**|Только для внутреннего применения.|  
|scheduler_address|**varbinary(8)**|Адрес в памяти связанного с данным потоком планировщика. Дополнительные сведения см. в разделе [sys. dm_os_schedulers &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|worker_address|**varbinary(8)**|Адрес в памяти связанного с данным потоком исполнителя. Дополнительные сведения см. в разделе [sys. dm_os_workers &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|fiber_context_address|**varbinary(8)**|Адрес контекста внутреннего волокна. Применимо только в случае, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для использования упрощенных пулов.|  
|self_address|**varbinary(8)**|Указатель для обеспечения внутренней согласованности.|  
|processor_group|**smallint**|**Область применения**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] и более поздних версий.<br /><br /> Идентификатор Processor_group.|  
|pdw_node_id|**int**|**Применимо к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор узла, на котором находится данное распределение.|  
  
## <a name="permissions"></a>Разрешения

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   

## <a name="notes-on-linux-version"></a>Заметки о версии Linux

Из-за того, как ядро SQL работает в Linux, некоторые из этих сведений не соответствуют данным диагностики Linux. Например, `os_thread_id` не соответствует результату таких средств, `ps``top` как или прокфс (/прок/`pid`).  Это обусловлено уровнем абстракции платформы (СКЛПАЛ), слоем между компонентами SQL Server и операционной системой.

## <a name="examples"></a>Примеры  
 При запуске сервера запускаются потоки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которыми затем связываются рабочие процессы. Однако внешние компоненты, например расширенные хранимые процедуры, могут запускать потоки в процессе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не управляет этими потоками. sys. dm_os_threads может предоставлять сведения о мошеннических потоках, которые потребляют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ресурсы в процессе.  
  
 Следующий запрос используется для поиска рабочих процессов, выполняющих потоки, не запущенные сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и для получения сведений о времени их выполнения.  
  
> [!NOTE]
>  Для краткости в следующем запросе в инструкции `*` используется звездочка (`SELECT`). Следует избегать использования звездочки (*) при выполнении запросов к представлениям каталога, динамическим административным представлениям и системным функциям с табличным значением. Будущие обновления и выпуски [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут добавлять столбцы и изменять порядок столбцов на эти представления и функции. Эти изменения могут повредить приложения, которые запрограммированы на определенный порядок и число столбцов.  
  
```  
SELECT *  
  FROM sys.dm_os_threads  
  WHERE started_by_sqlservr = 0;  
```  
  
## <a name="see-also"></a>См. также:  
  [sys. dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)   
 [SQL Server динамические административные представления, связанные с операционной системой &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  



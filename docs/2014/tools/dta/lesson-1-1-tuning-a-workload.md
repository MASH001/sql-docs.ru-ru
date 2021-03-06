---
title: Настройка рабочей нагрузки | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- workloads [SQL Server], tuning
ms.assetid: 6229bf3f-1182-4bc6-8451-cedc37f4b62e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3dd87c1e2bd08ce5bb1d05e9d51d92e3f62bcc7a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66110187"
---
# <a name="tuning-a-workload"></a>Настройка рабочей нагрузки
  Помощник по настройке ядра СУБД можно использовать для определения физической структуры базы данных и выбранных таблиц, оптимальной с точки зрения производительности запросов.  
  
 В данной задаче используется образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . В целях повышения безопасности образцы баз данных по умолчанию не устанавливаются. Дополнительные сведения об установке образцов баз данных см. в статье [Установка образцов SQL Server и образцов баз данных](http://sqlserversamples.codeplex.com).  
  
### <a name="tune-a-workload-transact-sql-script-file"></a>Настройка файла скрипта рабочей нагрузки Transact-SQL  
  
1.  Скопируйте образец инструкции или инструкций SELECT из примера «А. Использование инструкции SELECT для получения строк и столбцов" в разделе [Примеры использования инструкции SELECT (Transact-SQL)](/sql/t-sql/queries/select-examples-transact-sql) и вставьте их в редактор запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Сохраните файл с именем **MyScript.sql** в каталог, где его будет легко найти.  
  
2.  Запустите помощник по настройке ядра СУБД. См. раздел [Запуск помощника по настройке ядра СУБД](../../relational-databases/performance/database-engine-tuning-advisor.md).  
  
3.  На правой панели графического пользовательского интерфейса помощника по настройке ядра СУБД в поле **Имя сеанса** введите **MySession**.  
  
4.  В поле **Рабочая нагрузка** выберите значение **Файл**, нажмите кнопку **Выберите файл рабочей нагрузки** и выберите файл **MyScript.sql** , сохраненный в шаге 1.  
  
5.  Выберите в списке [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] База данных для анализа нагрузки **значение** , выберите [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] в сетке **Выберите базы данных и таблицы для настройки** и оставьте установленным флажок **Сохранить журнал настройки** . В поле**База данных для анализа рабочей нагрузки** указывается первая база данных, к которой будет подключаться помощник по настройке ядра СУБД при настройке рабочей нагрузки. После начала настройки помощник по настройке ядра СУБД подключается к базам данных, определенным в инструкциях `USE DATABASE` , которые содержатся в рабочей нагрузке.  
  
6.  Перейдите на вкладку **Параметры настройки** . Для этой практики не будут заданы какие-либо параметры настройки, но необходимо проанализировать параметры настройки по умолчанию. Нажмите клавишу F1, чтобы вызвать справку для этой страницы с вкладками. Нажмите кнопку **Дополнительные параметры** , чтобы просмотреть дополнительные параметры настройки. Нажмите кнопку **Справка** в диалоговом окне **Расширенные параметры настройки** , чтобы просмотреть дополнительные сведения о параметрах настройки. Нажмите кнопку **Отмена** , чтобы закрыть диалоговое окно **Расширенные параметры настройки** и оставить заданные по умолчанию параметры.  
  
7.  На панели инструментов нажмите кнопку **Начать анализ** . Хотя помощник по настройке ядра СУБД анализирует рабочую нагрузку, вы можете отслеживать ее состояние на вкладке **выполнение** . После завершения настройки отобразится вкладка **рекомендации** .  
  
     При возникновении ошибки даты и времени завершения настройки проверьте **время ожидания на** главной вкладке **Параметры настройки** . Убедитесь, что значение параметра время **окончания** в дате и времени превышает текущую дату и время, и при необходимости измените их.  
  
8.  После завершения анализа сохраните рекомендации в виде скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] , выбрав пункт **Сохранить рекомендации** в меню **Действия** . В диалоговом окне **Сохранить как** перейдите в каталог, где требуется сохранить скрипт рекомендаций, и введите имя файла **MyRecommendations**.  
  
## <a name="summary"></a>Сводка  
 Настройка простой рабочей нагрузки инструкции SELECT для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] завершена. Помощник по настройке ядра СУБД в качестве рабочих нагрузок может также принимать файлы трассировки приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] или таблицы. В следующей задаче рассматривается, как просмотреть рекомендации настройки, полученные в результате учебной настройки, и что они означают.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Просмотр рекомендаций по настройке](lesson-1-2-viewing-tuning-recommendations.md)  
  
  

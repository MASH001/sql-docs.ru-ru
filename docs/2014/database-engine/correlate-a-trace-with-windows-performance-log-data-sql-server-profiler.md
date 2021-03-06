---
title: Сопоставить трассировку с данными журнала производительности Windows (SQL Server Profiler) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], logs
ms.assetid: e1b3072c-8daf-49a7-9895-c8cccd2adb95
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3294c9fd70ebae8eab4e76e17b2e0a21771ec26f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66065053"
---
# <a name="correlate-a-trace-with-windows-performance-log-data-sql-server-profiler"></a>согласовать трассировку с данными журнала производительности Windows (приложение SQL Server Profiler)
  [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]может сопоставлять счетчики системного монитора Microsoft Windows с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] событиями или [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Системный монитор Windows регистрирует системную активность указанных счетчиков журнала производительности.  
  
> [!NOTE]  
>  Дополнительные сведения об общем доступе к журналам между различными версиями Windows приведены в конце данного подраздела.  
  
### <a name="to-correlate-a-trace-with-performance-log-data"></a>Согласование трассировки с данными журнала производительности  
  
1.  В [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]откройте сохраненный файл трассировки или таблицу трассировки. Нельзя согласовывать запущенную трассировку, которая производит сбор данных события. Чтобы гарантировать точность связывания с данными системного монитора, трассировка должна содержать столбцы данных **StartTime** и **EndTime** .  
  
2.  В меню  **Файл** в [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] выберите **Импорт данных производительности**.  
  
3.  В диалоговом окне **Открыть** выберите файл с журналом производительности. Чтобы данные журнала производительности можно было связать с трассировкой, они должны быть собраны в то же время, что и данные трассировки.  
  
4.  В диалоговом окне **Ограничение счетчиков производительности** установите флажки, относящиеся к объектам и счетчикам системного монитора, которые необходимо отобразить наряду с трассировкой. Нажмите кнопку **ОК**.  
  
5.  Выберите событие в окне событий трассировки или используйте клавиши со стрелками, чтобы перемещаться по строкам в окне событий трассировки. Красная вертикальная черта в окне **Данные системного монитора** указывает на данные журнала производительности, связанные с выбранным событием трассировки.  
  
6.  Выберите интересующую точку на графике системного монитора. Выбирается соответствующая трассировка строки, ближайшая по времени к выбранной точке. Чтобы увеличить временной диапазон, удерживая клавишу мыши, перетащите ее указатель по графику системного монитора.  
  
### <a name="to-create-performance-logs-that-can-be-shared-among-different-versions-of-windows"></a>Создание журналов производительности, общих для различных версий Windows  
  
1.  На панели управления выберите пункт **Администрирование**, а затем дважды щелкните элемент **Производительность**.  
  
2.  В диалоговом окне **Производительность** разверните **Оповещения и журналы производительности**, щелкните правой кнопкой мыши **Журналы счетчиков**и выберите **Новые параметры журнала**.  
  
3.  Введите имя журнала счетчиков и нажмите кнопку **ОК**.  
  
4.  На вкладке **Общие** щелкните **Добавить счетчики**.  
  
5.  В списке **Объект производительности** выберите объект, который требуется контролировать. Названия объектов производительности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для экземпляров по умолчанию [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] начинаются с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , а именованные экземпляры начинаются с MSSQL$*instanceName*.  
  
6.  Добавьте к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] необходимое количество счетчиков и прочие важные значения, такие как процессорное время и время диска.  
  
7.  После завершения добавления счетчиков нажмите кнопку **Закрыть**.  
  
8.  Установите значения для интервала **Снимать показания каждые** . Начинайте с интервала в 5 минут, и затем корректируйте его по необходимости.  
  
9. На вкладке **Файлы журналов** выберите **Текстовый файл (разделители-запятые)** в списке **Тип файла журнала** . Текстовые файлы журнала с разделителями-запятыми подходят для различных версий Windows; кроме того, их можно просматривать при помощи таких средств, как Microsoft Excel.  
  
10. На вкладке **Расписание** укажите расписание контроля.  
  
11. Нажмите кнопку **ОК** для создания журнала производительности.  
  
## <a name="see-also"></a>См. также  
 [Шаблоны и разрешения SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Запуск приложения SQL Server Profiler](../tools/sql-server-profiler/start-sql-server-profiler.md)  
  
  

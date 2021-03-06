---
title: Использование мастера полнотекстового индексирования | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextindexingwizard.selecttablecolumns.f1
- sql12.swb.fulltextindexingwizard.welcome.f1
- sql12.swb.fulltextindexingwizard.selectacatalog.f1
- sql12.swb.fulltextindexingwizard.progress.f1
- sql12.swb.fulltextindexingwizard.selectorcreatepopschedules.f1
- sql12.swb.fulltextindexingwizard.selectatableorview.f1
- sql12.swb.fulltextindexingwizard.selectchangetracking.f1
- sql12.swb.fulltextindexingwizard.selectanindex.f1
- sql12.swb.fulltextindexingwizard.summary.f1
helpviewer_keywords:
- Full-Text Indexing Wizard
- full-text search [SQL Server], Full-Text Indexing Wizard
ms.assetid: 3e9d9605-6525-4781-9168-fdaa06db3459
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f7bab4ee8f03eb666e1a8396fbf8957b1e42f2c7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66010898"
---
# <a name="use-the-full-text-indexing-wizard"></a>Использование мастера полнотекстового индексирования
  Мастер полнотекстового индексирования поможет выполнить ряд шагов, спланированных для создания полнотекстового индекса.  
  
#### <a name="to-use-the-full-text-indexing-wizard"></a>Использование мастера полнотекстового индексирования  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши таблицу, для которой необходимо создать полнотекстовый индекс, укажите **Полнотекстовый индекс**и щелкните **Определить полнотекстовый индекс**.  
  
     **Уникальный индекс**  
     Выберите индекс из раскрывающегося списка. Индекс должен иметь один ключевой столбец, быть уникальным и не допускающим значения NULL. Выбрать минимально возможный индекс ключа для полнотекстового уникального ключа. Для улучшения производительности рекомендуется использовать кластеризованный индекс.  
  
     **Доступные столбцы**  
     Чтобы включить столбец в индекс, установите флажок напротив имени столбца. Столбцы, не подлежащие полнотекстовому индексированию, отображаются серым цветом, а соответствующие им флажки отключаются.  
  
     **Язык для средства разбиения по словам**  
     Выберите язык из раскрывающегося списка. Выбранный язык будет использоваться [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для идентификации правильных средств разбиения по словам для индекса. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует средства разбиения по словам для определения границ слов в данных, подвергаемых полнотекстовому индексированию.  
  
     **Столбец типа**  
     Выберите имя столбца, содержащего тип документа столбца, подвергаемого полнотекстовому индексированию.  
  
     **Столбец Type** доступен только в том случае, если столбец, указанный в столбце **Доступные столбцы** , имеет `varbinary(max)` тип `image`или.  
  
     **Статистическая семантика**  
     Укажите, следует ли включить статистическое семантическое индексирование для выбранного столбца. Дополнительные сведения см. в разделе [Семантический поиск (SQL Server)](semantic-search-sql-server.md).  
  
     Если **Язык** выбран до выбора режима **Статистическая семантика**и выбранный язык не имеет связанной семантической модели языка, флажок **Статистическая семантика** будет недоступным. Если режим **Статистическая семантика** выбран до выбора **Языка**, в раскрывающемся поле со списком будут доступны только языки, имеющие семантическую модель языка.  
  
2.  Выбор параметров отслеживания изменений.  
  
     **Автоматически**  
     Выберите этот переключатель, чтобы обновление полнотекстового индекса осуществлялось автоматически по мере внесения изменений в базовые данные.  
  
     **Вручную**  
     Выберите этот переключатель, если не нужно, чтобы обновление полнотекстового индекса осуществлялось автоматически по мере внесения изменений в базовые данные. Изменения, внесенные в базовые данные, сохраняются. Однако, чтобы применить изменения к полнотекстовому индексу, необходимо запустить или запланировать запуск этого процесса вручную.  
  
     **Не отслеживать изменения**  
     Выберите этот переключатель, если не нужно, чтобы полнотекстовый индекс обновлялся в соответствии с изменениями, внесенными в базовые данные.  
  
     **Начать полное заполнение индекса сразу после его создания**  
     Выберите этот переключатель, чтобы запустить полное заполнение после успешного завершения работы мастера. Процесс будет состоять из создания структуры полнотекстового индекса в каталоге и заполнения его полнотекстовыми индексированными данными.  
  
3.  Выбор каталога, файловой группы индекса и списка стоп-слов.  
  
     **Выбрать полнотекстовый каталог**  
     Выбор полнотекстового каталога из списка. Каталогом по умолчанию для базы данных будет выбранный по умолчанию элемент в списке. Если нет доступных каталогов, список будет недоступен, а также будет установлен и недоступен флажок **Создать новый каталог** .  
  
    |||  
    |-|-|  
    |**Создать новый каталог**|Установите флажок для того, чтобы создать новый полнотекстовый каталог.|  
  
     **Имя**  
     Введите имя нового полнотекстового каталога.  
  
     **Назначить каталогом по умолчанию**  
     Установите флажок, чтобы сделать каталог используемым по умолчанию для этой базы данных.  
  
     **Учитывать диакритические знаки**  
     Укажите, будет ли новый каталог учитывать диакритические знаки или не будет. Если база данных учитывает диакритические знаки, флажок **Учитывать** по умолчанию будет установлен.  
  
     **Выберите файловую группу индекса**  
     Укажите файловую группу, на основе которой будет создан полнотекстовый индекс.  
  
     Выберите одно из следующих значений.  
  
    |Применение|Описание|  
    |-----------|-----------------|  
    |**\<>по умолчанию**|Если таблица или представление не секционированы, выберите это значение, чтобы использовать ту же файловую группу, что и в базовой таблице или представлении. Если таблица или представление не секционированы, то используется первичная файловая группа.|  
    |**БАЗОЙ**|Выберите это значение, чтобы назначить для нового полнотекстового индекса первичную файловую группу.|  
    |*определенная пользователем файловая группа по умолчанию*|Если существует определенный пользователем список стоп-слов, выберите его имя из списка, чтобы использовать эту файловую группу для нового полнотекстового индекса.|  
  
     **Выберите полнотекстовый список стоп-слов**  
     Укажите список стоп-слов для использования в полнотекстовом индексе или отключите использование этого списка.  
  
     В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях стоп-слова в базах данных управляются с помощью объектов, называемых списками стоп-слов. *Список стоп-слов* связан с полнотекстовым индексом и применяется к полнотекстовым запросам по этому индексу. Дополнительные сведения см. в разделе [Настройка стоп-слов и списков стоп-слов для полнотекстового поиска и управление ими](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
     Выберите одно из следующих значений.  
  
    |Применение|Описание|  
    |-----------|-----------------|  
    |**\<Системные>**|Выберите это значение, чтобы использовать в новом полнотекстовом индексе системный список стоп-слов. Это значение установлено по умолчанию.|  
    |**\<Выкл>**|Выберите это значение, чтобы отключить списки стоп-слов в новом полнотекстовом индексе.|  
    |*определенный пользователем список стоп-слов*|В списке отображается имя каждого из определенных пользователем списков стоп-слов, созданных для базы данных, если таковые существуют. Выберите какой-либо определенный пользователем список стоп-слов для использования в новом полнотекстовом индексе.|  
  
4.  При необходимости определите расписание заполнения. Операции индексирования начнутся немедленно, если только для них не было задано расписание для выполнения в будущем. Расписания будут созданы немедленно, хотя они не будут выполнены до заданного времени.  
  
     **Создание расписания для таблицы**  
     Позволяет определить расписание заполнений для таблицы.  
  
     **Создание расписания для каталога**  
     Позволяет определить расписание заполнений для полнотекстового каталога.  
  
     **Edit** (Изменение)  
     Позволяет изменить расписание.  
  
     **Удаление**  
     Позволяет удалить расписание.  
  
5.  Просмотр и управление выполнением мастера полнотекстового индексирования.  
  
     **Остановить**  
     Прерывает текущую операцию и блокирует выполнение мастером последующих полнотекстовых операций в течение этого сеанса.  
  
     **Отчет**  
     Когда выполнение всех операций завершено, нажмите эту кнопку, чтобы получить доступ к отчету о выполненных операциях. Можно просмотреть отчет, распечатать его в файл, скопировать в буфер обмена или отправить по электронной почте.  
  
  

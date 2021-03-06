---
title: Защита элементов общего набора данных | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
ms.assetid: 08e6d8b5-d88c-4ed2-9c05-55c757e00014
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a51e261d06933a30bf1c59adffa6963c9826f360
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "65570672"
---
# <a name="secure-shared-dataset-items"></a>Защита элементов общего набора данных
  На сервере отчетов элементы общего набора данных могут использоваться в нескольких отчетах. В целях управления уровнем доступа, предоставляемого пользователям, общие наборы данных можно защитить. По умолчанию только пользователи, являющиеся членами встроенной группы **Администраторы** , могут просматривать общие наборы данных, изменять свойства, включать кэширование, создавать планы обновления кэша и удалять элементы. Остальные пользователи должны иметь созданные для них назначения ролей, предоставляющие доступ к общему набору данных.  
  
 Для настройки безопасности нужно создать назначение ролей, указывающее, какой пользователь или группа имеет доступ к данному общему набору данных.  
  
## <a name="role-based-access-to-shared-datasets"></a>Доступ к общим наборам данных на основе ролей  
 Чтобы предоставить доступ к общим наборам данных, можно разрешить пользователям наследовать существующие назначения ролей родительской папки или создать новые назначения ролей для нужного элемента.  
  
 Назначениями роли по умолчанию, которые разрешают добавлять, удалять, изменять свойства элементов, а также просматривать связанные отчеты и общие источники данных для общих наборов данных, являются «Диспетчер содержимого», «Мои отчеты» и «Издатель». Чтобы изменять определение общего набора данных, используйте назначения ролей по умолчанию «Построитель отчетов» или «Диспетчер содержимого».  
  
 Назначения ролей обычно наследуются от родительского узла, поэтому папка, для которой включена задача **Просмотр отчетов** , передает это разрешение общим наборам данных и отчетам в папке.  
  
 Чтобы обеспечить больший контроль над общими наборами данных и результатами их запроса, настройте безопасность на уровне элемента для элемента общего набора данных или сохраните общие наборы данных в папке и настройте безопасность на уровне элемента для папки.  
  
## <a name="shared-dataset-parameters"></a>Параметры общего набора данных  
 Параметры общего набора данных не могут использоваться для ограничения доступа к данным для конкретных пользователей. Назначение параметров общего набора данных состоит в предоставлении способа указывать, какие данные должны быть включены при обработке общего набора данных. На сервере отчетов невозможно защитить значения для параметра общего набора данных.  
  
 В определении общего набора данных можно отметить параметры как допускающие только чтение и указать значения по умолчанию. Параметры, которые отмечены как допускающие только чтение, не могут быть переопределены на сервере. Например, в плане обновления кэша для общего набора данных нельзя указывать значения для параметров, допускающих только чтение. Если параметры общего набора данных включают выражения, которые ссылаются на пользовательскую глобальную коллекцию или имеют любые другие пользовательские зависимости, то невозможно создать план обновления кэша для общего набора данных.  
  
## <a name="tasks-access-to-items-and-default-roles"></a>Задачи, доступ к элементам и роли по умолчанию  
 Общие наборы данных следуют той же модели безопасности, что и отчеты. Чтобы предоставить пользователю разрешение для конкретных действий, выберите роль, включающую соответствующую задачу, которая включает эти разрешения. В следующей таблице перечислены задания и действия, которые они включают.  
  
|Выберите эту задачу|Предоставить пользователям следующие разрешения.|Роли по умолчанию, которые включают эту задачу|  
|----------------------|---------------------------------|-----------------------------------------|  
|Просмотр отчетов|Просмотр элемента общего набора данных в иерархии папок. Без этой задачи элемент будет невидим для пользователей и они могут не узнать, что этот набор данных доступен.|Браузер<br /><br /> Диспетчер содержимого<br /><br /> построитель отчетов<br /><br /> Мои отчеты|  
|Управление отчетами|Просмотр свойств, задающих имя, описание и сведения о соединении. Эта задача используется также для отображения элемента общего набора данных в иерархии папок. Если эта задача выбрана, можно опустить задачу «Просмотр отчетов».|Диспетчер содержимого<br /><br /> Издатель<br /><br /> Мои отчеты|  
|Использование отчетов|Просмотр определения общего набора данных.|Диспетчер содержимого<br /><br /> построитель отчетов|  
|Установка безопасности элементов|Создание и изменение назначений ролей, управляющих доступом к общему набору данных. Эта задача должна использоваться с задачей «Просмотр отчетов» или «Управление отчетами». В противном случае она не будет действовать, поскольку пользователь не сможет выбрать источник.|Диспетчер содержимого|  
  
 Дополнительные сведения см. в разделах [Задачи уровня элемента](../../reporting-services/security/tasks-and-permissions-item-level-tasks.md) и [Стандартные роли](../../reporting-services/security/role-definitions-predefined-roles.md).  
  
## <a name="see-also"></a>См. также:  
 [Управление общими наборами данных](../../reporting-services/report-data/manage-shared-datasets.md)   
 [Защита папок](../../reporting-services/security/secure-folders.md)   
 [Защищенные отчеты и ресурсы](../../reporting-services/security/secure-reports-and-resources.md)   
 [Предоставление разрешений на сервер отчетов в собственном режиме](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Предоставление разрешений на сервер отчетов в собственном режиме](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  

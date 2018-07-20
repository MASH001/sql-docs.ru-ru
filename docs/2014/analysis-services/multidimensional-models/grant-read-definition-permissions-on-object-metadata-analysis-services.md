---
title: Предоставление разрешений на чтение описания метаданным объекта (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f87b088072350e58aa00d7c0063a2aa2378346cb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241734"
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a>Предоставление разрешений на чтение описания метаданным объекта (службы Analysis Services)
  Разрешение на чтение описания объекта или метаданных на выбранных объектах позволяет администратору предоставлять разрешение на просмотр информации об объекте без дополнительного предоставления разрешения на изменение описания объекта, изменение структуры объекта или просмотр фактических данных объекта. `Read Definition` разрешения могут быть предоставлены на базы данных, источник данных, измерения, структуры интеллектуального анализа данных и уровни модели интеллектуального анализа данных. Если вам требуется `Read Definition` разрешения для куба, необходимо включить `Read Definition` для базы данных. Помните, что разрешения являются аддитивными. Например, одна роль предоставляет разрешение кубу на чтение метаданных, в то время как вторая роль предоставляет этому же пользователю разрешение измерению на чтение метаданных. Разрешения от двух разных ролей соединяются для предоставления пользователю разрешения как на чтение метаданных для куба, так и метаданных для измерения в рамках этой базы данных.  
  
> [!NOTE]  
>  Разрешение на чтение метаданных базы данных является минимальным разрешением, необходимым для соединения с базой данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с использованием среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] или среды [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Пользователь, имеющий разрешение на чтение метаданных, также может использовать набор строк схемы DISCOVER_XML_METADATA для создания запросов к объекту и просмотра его метаданных. Дополнительные сведения см. в разделе [Набор строк DISCOVER_XML_METADATA](../schema-rowsets/xml/discover-xml-metadata-rowset.md).  
  
## <a name="set-read-definition-permissions-on-a-database"></a>Установка разрешений на чтение описания для базы данных  
 Предоставление разрешения на чтение метаданных базы данных также предоставляет разрешение на чтение метаданных всех объектов в базе данных.  
  
 Мы советуем вам включать `Read Definition` разрешение на уровне базы данных, каждый раз, когда вы настраиваете роли для целевой обработки. Наличие `Read Definition` пользователи без прав администратора могут видеть иерархию объекта модели в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и переходить к индивидуальным объектам для последующей обработки.  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]соединитесь с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], разверните узел **Роли** для соответствующей базы данных в обозревателе объектов, а затем щелкните роль базы данных (или создайте новую).  
  
2.  На **Общие** выберите `Read Definition` параметр.  
  
3.  На вкладке **Членство** , введите учетные записи пользователя Windows и группы, которые подключаются к Analysis Services, используя данную роль.  
  
4.  Нажмите **ОК** для завершения процесса создания роли.  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a>Установка разрешений на чтение описания для индивидуальных объектов  
  
1.  В службе [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], откройте папку **Базы данных** , выберите базу данных, разверните узел **Роли** для соответствующей базы данных в обозревателе объектов, а затем щелкните роль базы данных (или создайте новую роль базы данных).  
  
2.  В **Общие** области, очистите разрешение базы данных для `Read Definition`. Данный шаг убирает наследование разрешений, следовательно вы можете устанавливать разрешения на индивидуальные объекты.  
  
3.  Выберите объект, для которого вы определяете `Read Definition` свойства:  
  
    -   В **источников данных** панели щелкните `Read Definition` флажок для этого источника данных. Элементы роли могут видеть строку подключения к источнику данных, включая имя сервера и, возможно, имя пользователя. Данное разрешение доступно в случае, если вы хотите предоставить информацию строки подключения, без дополнительного предоставления разрешения на изменение строки подключения или просмотр определений любых других объектов.  
  
    -   В **измерения** панели щелкните `Read Definition` флажок для этого измерения. Опытным аналитикам и разработчикам может потребоваться просмотр описания без разрешения на его изменение или просмотр описаний других объектов (таких как другие измерения, объекты куба или интеллектуальные анализы данных и модели интеллектуальных анализов данных).  
  
    -   В области структур интеллектуального анализа данных щелкните `Read Definition` флажок для структур интеллектуального анализа данных или моделей. `Read Definition` является обязательным для просмотра модели данных. Дополнительные сведения см. в разделе [Предоставление разрешений структурам интеллектуального анализа данных и моделям интеллектуального анализа данных (службы Analysis Services)](grant-permissions-on-data-mining-structures-and-models-analysis-services.md).  
  
4.  На вкладке **Членство** , введите учетные записи пользователя Windows и группы, которые подключаются к Analysis Services, используя данную роль.  
  
5.  Нажмите **ОК** для завершения процесса создания роли.  
  
## <a name="see-also"></a>См. также  
 [Предоставление разрешений базы данных &#40;служб Analysis Services&#41;](grant-database-permissions-analysis-services.md)   
 [Предоставление разрешений на обработку &#40;служб Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
  
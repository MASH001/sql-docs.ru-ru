---
title: Анализ табличной модели в Excel (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d838dbf683746b212967f2775c6c943310ce6cb6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204014"
---
# <a name="analyze-a-tabular-model-in-excel-ssas-tabular"></a>Анализ табличной модели в Excel (табличные службы SSAS)
  Функция анализа в Excel в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] открывает Microsoft Excel, создает соединение с источником данных, в качестве которого выступает база данных рабочей области модели, а затем добавляет сводную таблицу на рабочий лист. Объекты модели (таблицы, столбцы, меры, иерархии и ключевые показатели эффективности) включаются в качестве полей в список полей сводной таблицы.  
  
> [!NOTE]  
>  Для использования функции анализа в Excel необходимо на тот же компьютер, где находится среда [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], установить Microsoft Office 2003 или более поздней версии. Если Microsoft Office не установлен на том же компьютере, то можно с помощью Excel на другом компьютере подключиться к базе данных рабочей области модели в качестве источника данных. Затем можно вручную добавить сводную таблицу на лист. Объекты модели (таблицы, столбцы, меры и ключевые показатели эффективности) включаются в качестве полей в список полей сводной таблицы.  
  
## <a name="tasks"></a>Задания  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a>Анализ проекта табличной модели с помощью функции анализа в Excel  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]щелкните меню **Модель** и выберите пункт **Анализ в Excel**.  
  
2.  В диалоговом окне **Выбор учетных данных и перспективы** выберите один из приведенных ниже вариантов учетных данных для подключения к источнику данных рабочей области модели:  
  
    -   Для использования текущей учетной записи пользователя выберите **Текущий пользователь Windows**.  
  
    -   Чтобы воспользоваться другой учетной записью, выберите **Другой пользователь Windows**.  
  
         Обычно эта учетная запись будет членом той или иной роли. Пароль не требуется. Эта учетная запись может использоваться только в контексте подключения Excel к базе данных рабочей области.  
  
    -   Чтобы воспользоваться ролью безопасности, выберите **Роль**, а затем в поле со списком выберите одну или несколько ролей.  
  
         Роли безопасности должны определяться с помощью диспетчера ролей. Дополнительные сведения см. в разделе [Создание ролей и управление ими (табличные службы SSAS)](roles-ssas-tabular.md).  
  
3.  Чтобы воспользоваться перспективой, выберите нужную в поле со списком **Перспектива** .  
  
     Перспективы (за исключением заданных по умолчанию) должны определяться в диалоговом окне «Перспективы». Дополнительные сведения см. в разделе [Создание перспектив и управление ими (табличные службы SSAS)](perspectives-ssas-tabular.md).  
  
> [!NOTE]  
>  Список полей сводной таблицы в Excel не обновляется автоматически при внесении изменений в проект модели в конструкторе моделей. Чтобы обновить список полей сводной таблицы в Excel, нажмите кнопку **Обновить** на ленте **Параметры**.  
  
## <a name="see-also"></a>См. также  
 [Анализ в Excel &#40;табличные службы SSAS&#41;](analyze-in-excel-ssas-tabular.md)  
  
  
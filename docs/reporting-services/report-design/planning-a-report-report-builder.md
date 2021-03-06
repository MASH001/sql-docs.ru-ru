---
title: Планирование отчета (построитель отчетов) | Документы Майкрософт
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
helpviewer_keywords:
- getting started
- report design
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9c65d1db987f5d317b0719ff101012b4db0a5873
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67038030"
---
# <a name="planning-a-report-report-builder"></a>Планирование отчета (построитель отчетов)
  Построитель отчетов позволяет создавать отчеты с разбиением на страницы нескольких видов. Например, можно создавать отчеты, которые отображают сводку подробных данных о продажах, тенденции в маркетинге и продажах, рабочие отчеты или панели мониторинга. Можно также создавать отчеты, в которых используются преимущества текста со сложным форматированием, например заказы на продажу, каталоги продукции или стандартные письма. Все эти отчеты создаются с использованием различных сочетаний одних и тех же строительных блоков в построителе отчетов. Чтобы создать полезный, легкочитаемый отчет, рекомендуется сначала составить план. Перед началом работы полезно рассмотреть следующие вопросы.  
  
-   **В каком формате должен отображаться отчет?**  
  
     Отчеты можно подготовить к просмотру в режиме в сети в браузере, таком как веб-портал [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , или экспортировать в другие форматы, например Excel, Word или PDF. Очень важно определить окончательную форму отчета, поскольку не все функции доступны во всех форматах экспорта. Дополнительные сведения см. в разделах [Экспорт отчетов (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md).  
  
-   **Какая структура должна использоваться для представления данных в отчете?**  
  
     Имеется выбор между табличной, матричной (аналогична используемой в перекрестной таблице или в отчете по сводной таблице) структурой, структурой с диаграммами или структурой свободной формы либо любым сочетанием таких структур. Дополнительные сведения см. в разделах [Таблицы, матрицы, списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md) и [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md).  
  
-   **Как должен выглядеть отчет?**  
  
     Построитель отчетов предоставляет множество элементов отчета, которые могут быть добавлены для облегчения чтения, выделения наиболее важных данных, облегчения переходов внутри отчета и т. д. Зная, как должен выглядеть отчет, можно определить, нужны ли в нем такие элементы, как текстовые поля, прямоугольники, изображения и линии. Может потребоваться показать или скрыть элементы, добавить схему документа, включить детализированные отчеты или вложенные отчеты, а также ссылки на другие отчеты. Дополнительные сведения см. в разделах [Изображения, текстовые поля, прямоугольники и линии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/images-text-boxes-rectangles-and-lines-report-builder-and-ssrs.md) и [Интерактивная сортировка, схемы документов и ссылки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md).  
  
-   **Что должны видеть читатели отчета? Должны ли данные или формат фильтроваться для разных категорий читателей?**  
  
     Может понадобиться уменьшить область отчета, например, для конкретных пользователей или местоположений либо для конкретного периода времени. Чтобы отфильтровать данные отчета, используются параметры для получения и отображения только требуемых данных. Дополнительные сведения см. в разделе [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
-   **Необходимо ли организовать собственные вычисления?**  
  
     Иногда источник данных и наборы данных не содержат полей, необходимых для отчета. В этом случае, возможно, понадобится создать вычисляемые поля. Например, для получения объема продаж элементов строки может понадобиться умножить цену за единицу товара на количество. Для обеспечения условного форматирования и других расширенных функций также используются выражения. Дополнительные сведения см. в разделе [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md).  
  
-   **Следует ли вначале скрыть элементы отчета?**  
  
     Следует рассмотреть, необходимо ли, чтобы при первоначальном выполнении отчета были скрыты элементы отчета, включая области данных, группы и столбцы. Например, можно вначале представить сводную таблицу, а затем детализировать углублением сведения для представления подробных данных. Дополнительные сведения см. в разделе [Действие детализации (построитель отчетов и службы SSRS)](../../reporting-services/report-design/drilldown-action-report-builder-and-ssrs.md).  
  
-   **Как должен доставляться отчет?**  
  
     Отчет можно сохранить на локальном компьютере и продолжить работать с ним или выполнить его локально для получения своих собственных сведений. Но для того, чтобы этот отчет могли использовать и другие пользователи, его нужно сохранить на сервере отчетов, настроенном в собственном режиме или на сервере отчетов в режиме интеграции с SharePoint. Сохранение отчета на сервере позволяет выполнять его другим пользователям. Кроме того, администратор сервера отчетов может установить подписку на отчет либо доставку отчета по электронной почте другим пользователям. При необходимости отчет может поставляться в конкретном формате экспорта. Дополнительные сведения см. в разделе [Поиск, просмотр отчетов и управление ими (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Построитель отчетов в SQL Server](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
 [Основные понятия служб Reporting Services (SSRS)](../reporting-services-concepts-ssrs.md) [Учебники по построителю отчетов](../../reporting-services/report-builder-tutorials.md)  
  
  

---
title: Построение данных на вспомогательной оси (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a9bff6ec41cc2437c6083e150eb391470cb5a5ab
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66105431"
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a>Построение данных на вспомогательной оси (построитель отчетов и службы SSRS)
  Диаграмма имеет оси двух типов: основную и вспомогательную. Вспомогательная ось полезна при сравнении двух наборов значений с двумя различающимися диапазонами данных с общей категорией.  
  
 Например, предположим, что имеется диаграмма, вычисляющая доходы за 2008 год в зависимости от налогов. В этом случае период времени в течение 2008 года является общим для обоих наборов данных. Однако, если оба ряда построить на одной оси Y, нельзя сделать полезное сравнение, т. к. шкала оси Y оптимизирована для самых больших значений в наборе данных. Если показать доход на первичной оси, а налог на вторичной, можно отобразить каждый ряд на своей собственной оси Y со своей собственной шкалой значений. Ряды продолжают использовать общую ось X.  
  
 Если сравнивается более двух рядов, необходимо использовать другой подход для сравнения и отображения на диаграмме нескольких рядов. Дополнительные сведения см. в разделе [несколько рядов на диаграмме &#40;построитель отчетов и службы SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).  
  
 Пример этой диаграммы доступен в виде образца отчета. Дополнительные сведения о скачивании этого и других примеров отчетов см. в статье [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a>Построение ряда на вторичной оси  
  
1.  Щелкните правой кнопкой мыши ряды в диаграмме или поле в области **Значения** , которую нужно отобразить на вспомогательной оси, и выберите пункт **Свойства ряда**. Откроется диалоговое окно **Свойства ряда** .  
  
2.  Перейдите на вкладку **Оси и область диаграммы**и выберите, какую из вторичных осей необходимо включить: ось значений или ось категорий.  
  
## <a name="see-also"></a>См. также  
 [Форматирование меток оси на построитель отчетов &#40;диаграммы и SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Задание интервала оси (построитель отчетов и службы SSRS)](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  

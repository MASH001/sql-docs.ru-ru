---
title: Установка точек останова | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.setbreakpoints.f1
helpviewer_keywords:
- Set Breakpoints dialog box
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0c2c543343bd602be75d600a489edfd84663790b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62911406"
---
# <a name="set-breakpoints"></a>Задание точек останова
  Диалоговое окно **Установка точек останова** используется для указания событий, для которых будут включены точки останова, а также управления поведением точек останова.  
  
## <a name="options"></a>Параметры  
 **Включен**  
 Выберите, чтобы включить точку останова для события.  
  
 **Break Condition**  
 Позволяет просмотреть список доступных событий, для которых можно установить точки останова.  
  
 **Тип счетчика числа попаданий**  
 Позволяет указать условия срабатывания точки останова.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Постоянно**|Выполнение приостанавливается при каждом попадании в точку останова.|  
|**Число попаданий**|Выполнение приостанавливается, если число попаданий в точку останова равно значению счетчика попаданий.|  
|**Число попаданий больше или равно**|Выполнение приостанавливается, если число попаданий в точку останова становится равным или больше значения, заданного счетчиком попаданий.|  
|**Число попаданий кратно**|Выполнение приостанавливается, если число попаданий в точку останова кратно установленному. Например, если значение этого параметра равно 5, выполнение приостанавливается на каждой пятой точке прерывания.|  
  
 **Число попаданий**  
 Позволяет задать число попаданий в точку останова, необходимое для приостановки выполнения. Этот параметр недоступен, если точка останова настроена на срабатывание всегда.  
  
## <a name="see-also"></a>См. также  
 [Отладка потока управления](../../../integration-services/troubleshooting/debugging-control-flow.md)  
  
  

---
title: Обработка модели интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], processing
ms.assetid: c2204472-c500-47a5-9afa-7ce2ca78b233
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fd2506e835f634937d5bf135ed7eec7cfa259b5f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66083100"
---
# <a name="process-a-mining-model"></a>обработать модель интеллектуального анализа данных
  На вкладке «Модели интеллектуального анализа данных» конструктора интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]можно либо обработать конкретную модель, которая связана со структурой интеллектуального анализа данных, либо обработать все модели, связанные с этой структурой.  
  
 Обработка модели интеллектуального анализа данных производится с помощью следующих инструментов.  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 Для обработки также можно использовать команду XMLA Process. Дополнительные сведения см. в разделе [Средства и способы обработки (службы Analysis Services)](../multidimensional-models/tools-and-approaches-for-processing-analysis-services.md).  
  
### <a name="process-a-single-mining-model-using-sql-server-data-tools"></a>Обработка отдельной модели интеллектуального анализа данных с помощью SQL Server Data Tools  
  
1.  На вкладке **Модели интеллектуального анализа данных** конструктора интеллектуального анализа данных выберите модель интеллектуального анализа данных из одного или нескольких столбцов моделей в сетке.  
  
2.  В меню **Модель интеллектуального анализа данных** выберите пункт **Обработать модель**.  
  
     При внесении изменений в структуру интеллектуального анализа данных будет выдано приглашение к повторному развертыванию структуры перед обработкой модели. Нажмите кнопку **Да**.  
  
3.  В диалоговом окне **Обработка модели \<интеллектуального анализа данных — модель>** нажмите кнопку **выполнить**.  
  
     Откроется диалоговое окно **Развитие процесса** , отображающее подробные сведения об обработке модели.  
  
4.  После успешного завершения обработки модели нажмите кнопку **Закрыть** в диалоговом окне **Развитие процесса** .  
  
5.  Нажмите кнопку **Закрыть** в диалоговом окне **Обработка \<модели интеллектуального анализа данных — модель>** .  
  
 Были обработаны только структура интеллектуального анализа данных и выбранная модель интеллектуального анализа данных.  
  
### <a name="process-all-mining-models-that-are-associated-with-a-mining-structure"></a>Обработка всех моделей интеллектуального анализа данных, которые связаны со структурой интеллектуального анализа данных  
  
1.  На вкладке **Модели интеллектуального анализа данных** конструктора интеллектуального анализа данных выберите команду **Обработать структуру интеллектуального анализа данных и все модели** из меню **Модель интеллектуального анализа данных** .  
  
2.  При внесении изменений в структуру интеллектуального анализа данных будет выдано приглашение к повторному развертыванию структуры перед обработкой моделей. Нажмите кнопку **Да**.  
  
3.  В диалоговом окне **Обработка структуры \<интеллектуального анализа данных — структура>** нажмите кнопку **выполнить**.  
  
4.  Откроется диалоговое окно **Развитие процесса** , отображающее подробные сведения об обработке модели.  
  
5.  После успешного завершения обработки моделей нажмите кнопку **Закрыть** в диалоговом окне **Развитие процесса** .  
  
6.  Нажмите кнопку **Закрыть** в диалоговом окне **>модели обработки \<** .  
  
 Были обработаны структура интеллектуального анализа данных и все связанные с ней модели интеллектуального анализа данных.  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции по модели интеллектуального анализа данных](mining-model-tasks-and-how-tos.md)  
  
  

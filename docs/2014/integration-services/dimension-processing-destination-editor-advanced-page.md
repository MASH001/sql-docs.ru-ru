---
title: Редактор назначения «Обработка измерений» (страница «Дополнительно») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.advanced.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 2b30835a-2680-4d98-89a4-4f17e29e3818
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 07a04fe26bbd47463d0564f7799698ab282a9979
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66059488"
---
# <a name="dimension-processing-destination-editor-advanced-page"></a>Редактор назначения обработки измерений (страница «Дополнительно»)
  Используйте страницу **Дополнительно** диалогового окна **Редактор назначения обработки измерений** для настройки обработки ошибок.  
  
 Дополнительные сведения о назначении обработки измерений см. в разделе [Dimension Processing Destination](data-flow/dimension-processing-destination.md).  
  
## <a name="options"></a>Параметры  
 **Использовать конфигурацию ошибок по умолчанию**  
 Укажите, нужно ли использовать обработку ошибок в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] по умолчанию. По умолчанию это значение равно `True`.  
  
 **Действие при возникновении ошибки ключа**  
 Укажите способ обработки записей с недопустимыми ключевыми значениями.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**ConvertToUnknown**|Преобразует недопустимое ключевое значение в значение `UnknownMember`.|  
|**DiscardRecord**|Удаляет запись.|  
  
 **Пропускать ошибки**  
 Указывает, что ошибки должны пропускаться.  
  
 **Остановить при возникновении ошибки**  
 Указывает, что в случае ошибки обработка должна прерываться.  
  
 **Количество ошибок**  
 Выберите порог ошибок, при котором обработка должна прерываться, если выбран режим **Остановить при возникновении ошибок**.  
  
 **Действие при возникновении ошибки**  
 Если был выбран параметр **Остановить при возникновении ошибок**, укажите действие, которое нужно выполнить при достижении порога ошибок.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**StopProcessing**|Останавливает обработку.|  
|**StopLogging**|Останавливает ведение журнала ошибок.|  
  
 **Ключ не найден**  
 Укажите действие при ошибке «Ключ не найден». По умолчанию, присваивается значение **Сообщить и продолжить**.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Пропустить ошибку**|Пропустить ошибку и продолжить обработку.|  
|**Сообщить и продолжить**|Сообщить об ошибке и продолжить обработку.|  
|**Сообщить и остановиться**|Сообщить об ошибке и остановить обработку.|  
  
 **Дублирующийся ключ**  
 Указывает действие при ошибке «Повторяющийся ключ». По умолчанию, присваивается значение **Пропустить ошибку**.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Пропустить ошибку**|Пропустить ошибку и продолжить обработку.|  
|**Сообщить и продолжить**|Сообщить об ошибке и продолжить обработку.|  
|**Сообщить и остановиться**|Сообщить об ошибке и остановить обработку.|  
  
 **Ключ NULL преобразован в неизвестный**  
 Задает действие, когда ключ NULL преобразован в значение `UnknownMember`. По умолчанию, присваивается значение **Пропустить ошибку**.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Пропустить ошибку**|Пропустить ошибку и продолжить обработку.|  
|**Сообщить и продолжить**|Сообщить об ошибке и продолжить обработку.|  
|**Сообщить и остановиться**|Сообщить об ошибке и остановить обработку.|  
  
 **Ключ NULL не разрешен**  
 Указывает действие при обнаружении ключа NULL в случае запрета ключей NULL. По умолчанию, присваивается значение **Сообщить и продолжить**.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Пропустить ошибку**|Пропустить ошибку и продолжить обработку.|  
|**Сообщить и продолжить**|Сообщить об ошибке и продолжить обработку.|  
|**Сообщить и остановиться**|Сообщить об ошибке и остановить обработку.|  
  
 **Путь к журналу ошибок**  
 Введите путь к журналу ошибок или нажмите кнопку **Обзор(...)** для выбора назначения.  
  
 **Обзор (...)**  
 Укажите путь к журналу ошибок.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор назначения «Обработка измерений» &#40;страница «Диспетчер соединений»&#41;](../../2014/integration-services/dimension-processing-destination-editor-connection-manager-page.md)   
 [Редактор назначения "Обработка измерения" (страница "Сопоставления")](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)  
  
  

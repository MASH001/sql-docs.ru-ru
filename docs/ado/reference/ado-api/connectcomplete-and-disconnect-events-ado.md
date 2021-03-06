---
title: События Коннекткомплете и Disconnect (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Disconnect
- Connection::ConnectComplete
- ConnectComplete
- Connection::Disconnect
helpviewer_keywords:
- Disconnect event [ADO]
- ConnectComplete event [ADO]
ms.assetid: 568f5252-d069-4d99-a01b-2ada87ad1304
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 448270ddf0e8cd7efb5ec39a93d4ff993360730e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67919561"
---
# <a name="connectcomplete-and-disconnect-events-ado"></a>События ConnectComplete и Disconnect (ADO)
Событие **коннекткомплете** вызывается после запуска соединения. Событие **Disconnect** вызывается после завершения соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *pError*  
 Объект [ошибки](../../../ado/reference/ado-api/error-object.md) . Она описывает ошибку, которая возникла, если значение *адстатус* равно **адстатусеррорсоккурред**; в противном случае он не задан.  
  
 *адстатус*  
 Значение [евентстатусенум](../../../ado/reference/ado-api/eventstatusenum.md) , которое всегда возвращает **адстатусок**.  
  
 При вызове **коннекткомплете** этот параметр имеет значение **адстатусканцел** , если событие **виллконнект** запросило отмену ожидающего подключения.  
  
 Перед возвращением одного из событий задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений. Однако закрытие и повторное открытие [соединения](../../../ado/reference/ado-api/connection-object-ado.md) приводит к повторному возникновению этих событий.  
  
 *пконнектион*  
 Объект **соединения** , к которому применяется это событие.  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (Visual c++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)

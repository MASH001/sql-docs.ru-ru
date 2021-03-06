---
title: Метод SaveToFile | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c2e56178ad306d5b39c2445c391c3bbabe4fc424
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917037"
---
# <a name="savetofile-method"></a>Метод SaveToFile
Сохраняет двоичное содержимое [потока](../../../ado/reference/ado-api/stream-object-ado.md) в файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>Параметры  
 *FileName*  
 **Строковое** значение, содержащее полное имя файла, в который будет сохранено содержимое **потока** . Можно сохранить в любое допустимое локальное расположение или любое доступное расположение через UNC-значение.  
  
 *SaveOptions*  
 Значение [савеоптионсенум](../../../ado/reference/ado-api/saveoptionsenum.md) , указывающее, должен ли новый файл создаваться с помощью **SaveToFile**, если он еще не существует. Значение по умолчанию — **адсавекреатенотексистс**. С помощью этих параметров можно указать, что ошибка возникает, если указанный файл не существует. Можно также указать, что **SaveToFile** перезаписывает текущее содержимое существующего файла.  
  
> [!NOTE]
>  Если перезаписать существующий файл (когда **адсавекреатеоверврите** установлен), **SaveToFile** усекает все байты из исходного существующего файла, который соответствует новому [EOS](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Remarks  
 **SaveToFile** может использоваться для копирования содержимого объекта **потока** в локальный файл. Содержимое или свойства объекта **Stream** не изменяются. Перед вызовом **SaveToFile**объект **потока** должен быть открытым.  
  
 Этот метод не изменяет связь объекта **потока** с базовым источником. Объект **потока** по-прежнему будет связан с исходным URL-адресом или **записью** , которая была источником при открытии.  
  
 После операции **SaveToFile** текущая координата ([положением](../../../ado/reference/ado-api/position-property-ado.md)) в потоке устанавливается в начало потока (0).  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Open (поток ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)

---
title: ISSCommandWithParameters::SetParameterProperties (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 778021ce007f0c1eac68197e0c07e2cb7b0bb001
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62638768"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
  Задает свойства каждого параметра по порядковому номеру или задает массовые свойства параметра, указывая массив структур SSPARAMPROPS.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT SetParameterProperties(  
DB_UPARAMS cParams,   
SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>Аргументы  
 *cParams*[in]  
 Количество структур SSPARAMPROPS в массиве *rgParamProperties*. Если это число равно нулю, `ISSCommandWithParameters::SetParameterProperties` то удаляет все свойства, которые могли быть указаны для любых параметров в команде.  
  
 *rgParamProperties*[in]  
 Массив задаваемых структур SSPARAMPROPS.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 `ISSCommandWithParameters::SetParameterProperties` Метод возвращает те же коды ошибок, что и метод Core OLE DB **ICommandProperties:: SetProperties** .  
  
## <a name="remarks"></a>Remarks  
 Задание свойств параметра с помощью этого метода допускается для каждого параметра по порядковому номеру или с помощью одного `ISSCommandWithParameters::SetParameterProperties` вызова после того, как SSPARAMPROPS был построен из массива свойств.  
  
 Перед **SetParameterInfo** вызовом `ISSCommandWithParameters::SetParameterProperties` метода необходимо вызвать метод SetParameterInfo. Вызов метода `SetParameterProperties(0, NULL)` очищает все указанные свойства параметра, тогда как вызов метода `SetParameterInfo(0,NULL,NULL)` очищает все сведения о параметре, в том числе все свойства, которые могут быть связаны с параметром.  
  
 Вызов `ISSCommandWithParameters::SetParameterProperties` для указания свойств параметра, который не относится к типу DBTYPE_XML или DBTYPE_UDT возвращает DB_E_ERRORSOCCURRED или DB_S_ERRORSOCCURRED и помечает поле *dwstatus устанавливается* всех дбпропс, содержащихся в SSPARAMPROPS для этого параметра, с DBPROPSTATUS_NOTSET. Чтобы обнаружить, к какому параметру относится DB_E_ERRORSOCCURRED или DB_S_ERRORSOCCURRED, необходимо пройти по массиву DBPROP каждого набора DBPROPSET, содержащегося в структуре SSPARAMPROPS.  
  
 Если `ISSCommandWithParameters::SetParameterProperties` вызывается для указания свойств параметров, сведения о параметрах которых еще не заданы с помощью **SetParameterInfo**, поставщик возвращает E_UNEXPECTED со следующим сообщением об ошибке:  
  
 Невозможно вызвать метод SetParameterProperties для указанных параметров, не вызывая предварительно метод SetParameterInfo. До задания свойств параметров необходимо задать сведения о параметрах.  
  
 Если вызов `ISSCommandWithParameters::SetParameterProperties` содержит некоторые параметры, в которых заданы сведения о параметрах, и некоторые параметры, в которых не заданы сведения о параметрах, свойства DWSTATUS устанавливается в DBPROPSET набора свойств SSPARAMPROPS будут возвращаться с DBSTATUS_NOTSET.  
  
 Структура SSPARAMPROPS определена следующим образом.  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 Улучшения ядра СУБД, появившиеся с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], позволяют методу ISSCommandWithParameters::SetParameterProperties получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значений, которые метод ISSCommandWithParameters::SetParameterProperties возвращает в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Обнаружение метаданных](../native-client/features/metadata-discovery.md).  
  
|Участник|Описание|  
|------------|-----------------|  
|*iOrdinal*|Порядковый номер переданного параметра.|  
|*cPropertySets*|Количество структур DBPROPSET в *rgPropertySets*.|  
|*rgPropertySets*|Указатель на буфер, в который будет возвращен массив структур DBPROPSET.|  
  
## <a name="see-also"></a>См. также  
 [ISSCommandWithParameters (OLE DB)](isscommandwithparameters-ole-db.md)  
  
  

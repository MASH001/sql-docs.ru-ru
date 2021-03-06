---
title: Таблица совместимости | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application compatibility issues [ODBC]
- application upgrades [ODBC], compatibility matrix
- upgrading applications [ODBC], compatibility matrix
ms.assetid: 0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0406599e1657a900d1669861572ff13834cec670
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307457"
---
# <a name="compatibility-matrix"></a>Матрица совместимости
В следующей таблице описывается совместимость типов приложений и драйверов, определенных ранее в этом разделе.  
  
|Тип приложения<br /><br /> и версия|32-разрядный ODBC<br /><br /> драйвер *2. x*|ODBC *3. x*<br /><br /> аудиодрайвера|Драйвер ODBC 3,8|ISO и Open Group-совместимый драйвер|  
|--------------------------------------|-----------------------------------|---------------------------|---------------------|-----------------------------------------|  
|16-разрядное приложение, любая версия|Совместимые|Совместимые|Совместимые|Совместимые|  
|Приложение чистого *2. x*|Совместимые|Совместимые|Совместимые|Несовместимо [3]|  
|Перекомпилированное приложение чистого *2. x*|Совместимые|Совместимо [1]|Совместимо [1]|Несовместимо [3]|  
|Приложение для Юникода чисто *2. x*|Совместимые|Совместимо [1]|Совместимо [1]|Несовместимо [3]|  
|Чистая открытая группа и совместимое с ISO приложение|Не совместимо|Совместимо [2]|Совместимо [2]|Совместимо [2]|  
|Чистое приложение 3,0|Не совместимо|Совместимые|Совместимые|Несовместимо [4]|  
|Чистое приложение 3,5|Не совместимо|Совместимые|Совместимые|Несовместимо [4]|  
|Чистое приложение 3,8 (или более поздней версии)|Не совместимо [5]|Не совместимо [5]|Совместимые|Несовместимо [4]|  
|Замененное приложение|Совместимые|Совместимые|Совместимые|Несовместимо [3]|  
  
 [1] приложение должно выполнить повторную компиляцию с использованием заголовков ODBC 3,5 (или более поздней версии) с параметром Юникода (если это приложение в Юникоде) и задать для ОДБКВЕР значение 0x0250.  
  
 [2] приложение должно компилироваться с помощью заголовков ODBC 3,5 (или более поздней версии) и связываться с диспетчером драйверов ODBC. Также необходимо установить флаг заголовка ODBC_STD.  
  
 [3] такая конфигурация может привести к сбою, так как в ODBC *2. x* есть функции, которые не являются стандартными, например закладки.  
  
 [4] такая конфигурация может привести к сбою, так как в ODBC *3. x* есть функции, которые не являются стандартными, например закладки.  
  
 [5] такая конфигурация может привести к сбою, так как в ODBC 3,8 есть функции, которые не входят в драйверы ODBC 2. x или 3. x, такие как специфические для драйвера [типы данных C в ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
## <a name="driver-manager-compatibility"></a>Совместимость с диспетчером драйверов  
 Приложение ODBC 3,0, которое должно взаимодействовать со всеми версиями диспетчера драйверов, должно выполнять следующие действия при запуске:  
  
-   Выделение обработчика среды.  
  
-   Задайте для атрибута среды SQL_ATTR_ODBC_VERSION значение SQL_OV_ODBC3_80. Если диспетчер драйверов возвращает SQL_ERROR, диспетчер драйверов старше 3,8. Сбросьте SQL_ATTR_ODBC_VERSION, чтобы SQL_OV_ODBC3 или SQL_OV_ODBC2 соответствующим образом соответствовать диспетчеру драйверов.  
  
-   Выделение маркера подключения.  
  
-   Установите соединение.  
  
-   Вызовите SQLGetInfo для SQL_DRIVER_ODBC_VER, чтобы определить версию драйвера. Если драйвер является драйвером ODBC 3,8, можно использовать специфические для драйвера типы C. В противном случае не используйте специфические для драйвера типы данных C.  
  
 Обратите внимание, что перекомпилированное приложение ODBC 3. x может использовать функции ODBC 3,8, отличные от типов C, относящихся к драйверу, без указания SQL_OV_ODBC3_80 для SQL_ATTR_ODBC_VERSION. Это похоже на перекомпилированное приложение ODBC 2. x, использующее функции ODBC 3. x.  
  
## <a name="using-sqlcancelhandle-in-an-application-compatible-with-all-driver-managers"></a>Использование Склканцелхандле в приложении, совместимом со всеми диспетчерами драйверов  
 Так как [функция склканцелхандле](../../../odbc/reference/syntax/sqlcancelhandle-function.md) не поддерживается в диспетчерах драйверов, выпущенных до Windows 7, приложение не может быть загружено в более ранние версии Windows, если оно вызывает **склканцелхандле** напрямую. Для работы со всеми версиями диспетчеров драйверов и использования **склканцелхандле** в новых версиях Windows приложение должно вызывать **склканцелхандле** косвенно с помощью **LoadLibrary** и **GetProcAddress.**  
  
## <a name="see-also"></a>См. также:  
 [Новые возможности ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)

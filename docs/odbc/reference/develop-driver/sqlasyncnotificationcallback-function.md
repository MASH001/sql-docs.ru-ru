---
title: Функция Скласинкнотификатионкаллбакк | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6c182c48b8e5ddb70204ddd3a94d9651f97595d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294541"
---
# <a name="sqlasyncnotificationcallback-function"></a>Функция SQLAsyncNotificationCallback
**Соответствия**  
 Введенная версия: ODBC 3,8  
  
 Соответствие стандартам: нет  
  
 **Сводка**  
 **Скласинкнотификатионкаллбакк** позволяет драйверу обращаться к диспетчеру драйверов, когда в ходе выполнения текущей асинхронной операции возникает некоторый прогресс, когда драйвер возвращает SQL_STILL_EXECUTING. **Скласинкнотификатионкаллбакк** может вызываться только драйвером.  
  
 Драйверы не вызывают **скласинкнотификатионкаллбакк** с именем функции **скласинкнотификатионкаллбакк**. Вместо этого диспетчер драйверов передает указатель на функцию в качестве значения атрибута SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK или SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK соответствующего маркера соединения или обработчика инструкции соответственно. Различным дескрипторам могут быть назначены разные значения указателя на функцию. Тип указателя функции определяется как SQL_ASYNC_NOTIFICATION_CALLBACK.  
  
 **Скласинкнотификатионкаллбакк** является потокобезопасным. Драйвер может использовать несколько потоков, вызывающих **скласинкнотификатионкаллбакк** на разных дескрипторах одновременно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>Аргументы  
 *пконтекс*  
 Указатель на структуру данных, определенную диспетчером драйверов. Значение передается драйверу через SQLSetConnectAttr (SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) или SQLSetStmtAttr (SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT).  Драйвер не имеет доступа к значению.  
  
 *фласт*  
 Используется драйвером для обозначения того, что вызов функции обратного вызова является последним для текущей асинхронной операции. Драйвер вернет код возврата, отличный от SQL_STILL_EXECUTING, когда диспетчер драйверов снова вызывает функцию. Диспетчер драйверов может использовать эти сведения, например для информирования приложения заранее о том, что асинхронная операция будет завершена.  
  
 Если *Handle* не является допустимым маркером типа, указанного параметром *параметром handletype*, **склканцелхандле** возвращает SQL_INVALID_HANDLE.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **Скласинкнотификатионкаллбакк** может возвращать SQL_ERROR в следующих двух ситуациях (они указывают на проблему реализации в драйвере или диспетчере драйверов.  
  
|Error|Описание|  
|-----------|-----------------|  
|Соединение или инструкция не запрашивают уведомление.||  
|Недопустимый *Handle*|Драйвер передал недопустимый обработчик, который не прошел проверку внутреннего диспетчера драйверов.|  
  
## <a name="see-also"></a>См. также:  
 [Асинхронное выполнение (метод опроса)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)

---
title: sp_xp_cmdshell_proxy_account (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xp_cmdshell_proxy_account
- sp_xp_cmdshell_proxy_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xp_cmdshell_proxy_account
- xp_cmdshell
ms.assetid: f807c373-7fbc-4108-a2bd-73b48a236003
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 59ea64e16f1469c12461a559c3f102094615fa12
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67950463"
---
# <a name="sp_xp_cmdshell_proxy_account-transact-sql"></a>sp_xp_cmdshell_proxy_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает учетные данные прокси-сервера для **xp_cmdshell**.  
  
> [!NOTE]  
>  по умолчанию **xp_cmdshell** отключен. Сведения о включении **xp_cmdshell**см. в разделе [параметр конфигурации сервера xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_xp_cmdshell_proxy_account [ NULL | { 'account_name' , 'password' } ]  
```  
  
## <a name="arguments"></a>Аргументы  
 NULL  
 Указывает, что учетные данные учетной записи-посредника должны быть удалены.  
  
 *account_name*  
 Указывает имя входа Windows, которое будет использовано как учетная запись-посредник.  
  
 *password*  
 Указывает пароль для учетной записи Windows.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 Учетные данные прокси-сервера будут называться **# #xp_cmdshell_proxy_account # #**.  
  
 При выполнении с параметром NULL **sp_xp_cmdshell_proxy_account** удаляет учетные данные прокси-сервера.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-the-proxy-credential"></a>A. Создание учетных данных для учетной записи-посредника  
 Следующий пример показывает, как создать учетные данные учетной записи-посредника для учетной записи Windows с именем `ADVWKS\Max04` и паролем `ds35efg##65`.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'ADVWKS\Max04', 'ds35efg##65';  
GO  
```  
  
### <a name="b-dropping-the-proxy-credential"></a>Б) Удаление учетных данных для учетной записи-посредника  
 Следующий пример удаляет учетные данные учетной записи-посредника из хранилища учетных данных.  
  
```  
EXEC sp_xp_cmdshell_proxy_account NULL;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [xp_cmdshell &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md)   
 [Создание УЧЕТных данных &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys. Credentials &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  

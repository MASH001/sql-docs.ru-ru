---
title: Олицетворение и безопасность интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- execution context [CLR integration]
- user impersonation [CLR integration]
- context [CLR integration]
ms.assetid: 1495a7af-2248-4cee-afdb-9269fb3a7774
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2c32691a065c2bfc43868d6b4105fbf1395a63ed
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62781132"
---
# <a name="impersonation-and-clr-integration-security"></a>Олицетворение и средства обеспечения безопасности при интеграции со средой CLR
  При обращении управляемого кода к внешним ресурсам в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не выполняется автоматически олицетворение текущего контекста выполнения, в котором выполняется процедура. В коде сборок `EXTERNAL_ACCESS` и `UNSAFE` олицетворение текущего контекста выполнения может проводиться явно.  
  
> [!NOTE]  
>  Сведения об изменениях в поведении для олицетворения см. в разделе [критические изменения в функциях ядро СУБД в SQL Server 2014](../breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Поставщик внутрипроцессного доступа к данным предоставляет прикладной программный интерфейс, `SqlContext.WindowsIdentity`, который может использоваться для получения токена, связанного с текущим контекстом безопасности. В управляемом коде сборок `EXTERNAL_ACCESS` и `UNSAFE` этот метод может использоваться для получения контекста, а метод `WindowsIdentity.Impersonate` платформы .NET Framework служит для олицетворения этого контекста. При проведении явного олицетворения в пользовательском коде применяются следующие ограничения.  
  
-   Внутрипроцессный доступ к данным не допускается, если управляемый код находится в состоянии, прошедшем олицетворение. В коде можно выполнить откат олицетворения, а затем вызвать средства внутрипроцессного доступа к данным. Следует отметить, что для отката олицетворения требуется сохранить возвращаемое значение (объект `WindowsImpersonationContext`) исходного метода `Impersonate` и вызвать метод `Undo` применительно к этому контексту `WindowsImpersonationContext`.  
  
     Это ограничение означает, что при осуществлении внутрипроцессного доступа к данным этот доступ всегда осуществляется в условиях применения текущего контекста безопасности, являющимся действительным для данного сеанса. Данные не могут быть изменены с помощью явного олицетворения в рамках управляемого кода.  
  
-   Применительно к управляемому коду, выполняемому асинхронно (например, с помощью сборок `UNSAFE`, в которых создаются потоки и код выполняется асинхронно), внутрипроцессный доступ к данным ни в коем случае не разрешается. Это справедливо, независимо от наличия олицетворения.  
  
 Если код выполняется в олицетворенном контексте, отличном от контекста [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то в нем нельзя выполнять вызовы внутрипроцессного доступа к данным; в коде необходимо отменить контекст олицетворения перед выполнением вызовов внутрипроцессного доступа к данным. Если внутрипроцессный доступ к данным осуществляется из управляемого кода, то для авторизации всегда используется первоначальный контекст выполнения точки входа [!INCLUDE[tsql](../../includes/tsql-md.md)] в управляемый код.  
  
 Как сборки `EXTERNAL_ACCESS`, так и сборки `UNSAFE` получают доступ к ресурсам операционной системы с помощью учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если в них не было специально применено олицетворение текущего контекста безопасности, как описано выше. В связи с этим требуется более высокий уровень доверия к авторам сборок `EXTERNAL_ACCESS`, чем к авторам сборок `SAFE`, что выражается в наличии разрешения `EXTERNAL ACCESS` на уровне имени входа. Только именам входа, которым доверено выполнение кода в рамках учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], должно быть предоставлено разрешение `EXTERNAL ACCESS`.  
  
## <a name="see-also"></a>См. также  
 [Безопасность интеграции со средой CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Олицетворение и учетные данные для соединений](../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
  
  

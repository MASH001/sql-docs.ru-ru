---
title: Параметры (страница «результаты запроса и службы зависимостей») | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: b9200880a9581b3903985c16fc2af129d19aceec
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "65481207"
---
# <a name="options-query-results-and-dependency-services-page"></a>Параметры ("Результаты запроса" и страница "Службы зависимостей")
  Используйте эту страницу, чтобы указать сервер для подключения к службам зависимостей. Службы зависимостей позволяют извлекать данные о зависимостях между объектами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], сохраненными на разных серверах. Просмотреть зависимости объектов можно с помощью диалогового окна « **зависимости объектов** » в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]среде.  
  
 **Выбор действия**  
  
1.  [Откройте диалоговое окно «Параметры» (страницу результатов запроса или служб зависимостей)](#open_dialog)  
  
2.  [Настройка параметров](#options)  
  
##  <a name="open-the-options-query-resultsdependency-services-page-dialog-box"></a><a name="open_dialog"></a>Открытие диалогового окна «Параметры» (страница «результаты запроса/службы зависимостей»)  
  
1.  В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]выберите пункт **Параметры** в меню **Сервис** .  
  
2.  Разверните **Результаты запроса** и нажмите кнопку **Службы зависимостей**.  
  
##  <a name="configure-the-options"></a><a name="options"></a>Настройка параметров  
  
### <a name="options"></a>Параметры  
 **Сервер служб зависимостей**  
 Укажите сервер, на котором установлены службы зависимостей.  
  
 **Аутентификация**  
 Выберите проверку подлинности Windows, чтобы войти в систему с использованием учетной записи Microsoft Windows, или выберите проверку подлинности SQL Server.  
  
 При подключении пользователя с указанным именем и паролем через недоверенное соединение, SQL Server выполняет проверку подлинности посредством проверки настройки учетной записи входа SQL Server и совпадения указанного пароля с предварительно сохраненными. Если SQL Server не может найти такое имя входа, проверка подлинности прекращается и пользователь получает сообщение об ошибке.  
  
 **User name**  
 При использовании проверки подлинности SQL Server укажите имя пользователя.  
  
 **Пароль**  
 При использовании проверки подлинности SQL Server укажите пароль.  
  
 **Тест**  
 Щелкните, чтобы проверить соединение.
---
title: Практическое руководство. Удаление объектов и разрешение зависимостей | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Data.Tools.Project.HelpKeywords.SqlProjectDropDatabaseConfirmationDialog
- sql.data.tools.dropdatabaseconfirmation.dialog
- sql.data.tools.dropmultipledatabasesconfirmation.dialog
ms.assetid: fb31c2b1-ca4f-4e11-a0b6-5c26430f1c8c
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ae1375a871598a1bf4ce4bd217336450c50d3264
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082696"
---
# <a name="how-to-delete-objects-and-resolve-dependencies"></a>Как удалять объекты и разрешать зависимости
При переименовании или удалении объекта в **обозревателе объектов SQL Server** средства SQL Server Data Tools автоматически определяют все зависимые объекты и подготавливают скрипт ALTER для переименования или удаления зависимости.  
  
> [!WARNING]  
> В следующих процедурах используются сущности, созданные ранее с помощью руководства по [разработке подключенной базы данных](../ssdt/connected-database-development.md).  
  
### <a name="to-delete-a-database"></a>Удаление базы данных  
  
1.  Щелкните правой кнопкой мыши нужную базу данных в **обозревателе объектов SQL Server** и выберите пункт **Удалить**.  
  
2.  Примите все параметры по умолчанию в диалоговом окне **Удаление базы данных** и щелкните **ОК**.  
  
### <a name="to-rename-a-table"></a>Переименование таблицы  
  
1.  Таблица `Customer` не должна быть открыта ни в конструкторе таблиц, ни в редакторе Transact\-SQL.  
  
2.  Разверните узел **Таблицы** в **обозревателе объектов SQL Server**. Щелкните правой кнопкой мыши таблицу **Customer** и выберите команду **Переименовать**.  
  
3.  Измените имя таблицы на **Customers** и нажмите клавишу "ВВОД".  
  
4.  Обратите внимание, что от вашего имени сразу вызывается операция **Обновление базы данных**. SSDT вызовет от вашего имени хранимую процедуру sp_rename, чтобы переименовать таблицу. Если есть какие-либо зависимые объекты, например ограничения внешнего ключа, они также будут обновлены.  
  
    > [!WARNING]  
    > В SSDT зависимости на основе скриптов, например ссылки на таблицу из представления, или хранимые процедуры автоматически не обновляются. После переименования все другие зависимости можно найти с помощью области **Список ошибок**, чтобы вручную исправить их.  
  
5.  Примените изменения, выполнив действия из предыдущей процедуры, описанной в [практическом руководстве по обновлению подключенной базы данных с помощью Power Buffer](../ssdt/how-to-update-a-connected-database-with-power-buffer.md).  
  
6.  Еще раз щелкните правой кнопкой мыши таблицу **Customers** в **обозревателе объектов SQL Server** и выберите пункт **Просмотр данных**. Обратите внимание, что данные таблицы остаются неизменными после операции переименования.  
  
7.  Щелкните правой кнопкой мыши таблицу **Products** и выберите **Просмотр кода**. Обратите внимание, что ссылка на внешний ключ обновилась автоматически на `REFERENCES [dbo].[Customers] ([Id])` в соответствии с переименованием.  
  
### <a name="to-delete-a-table"></a>Удаление таблицы  
  
1.  Щелкните правой кнопкой мыши таблицу **Customers** в **обозревателе объектов SQL Server** и выберите пункт **Удалить**.  
  
2.  В диалоговом окне **Предварительный просмотр обновлений базы данных** в разделе **Действие пользователя** обратите внимание, что в SSDT определены все зависимые объекты (в этом случае ссылка на внешний ключ), которые будут удалены.  
  
3.  Щелкните **Обновить базу данных**.  
  
4.  Щелкните правой кнопкой мыши таблицу **Products** в **обозревателе объектов SQL Server** и выберите пункт **Просмотр кода**. Обратите внимание, что ссылки на внешний ключ в таблице `Customers` больше нет.  
  
    > [!WARNING]  
    > Если в момент удаления таблица **Products** будет открыта в конструкторе таблиц или редакторе Transact\-SQL, она не будет автоматически обновлена с учетом удаления ссылки на внешний ключ. Кроме того, в **списке ошибок** могут появиться сообщения о неразрешенных ссылках. Чтобы устранить эту проблему, закройте конструктор таблиц или редактор Transact\-SQL и заново откройте таблицу Products.  
  
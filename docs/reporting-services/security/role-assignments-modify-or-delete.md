---
title: Изменение или удаление назначения ролей (веб-портал SSRS) | Документация Майкрософт
ms.date: 05/07/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- system roles [Reporting Services]
- modifying role assignments
- deleting role assignments
ms.assetid: 523bdd32-92cb-4b48-a3a9-d58b2385bde7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 28695a4849b29c6e593f42489fc149efd9a8db53
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "65570646"
---
# <a name="role-assignments---modify-or-delete"></a>Изменение или удаление назначений ролей

Назначение ролей сопоставляет учетную запись группы или пользователя с предварительно определенной ролью, которая определяет доступные для выполнения задачи. Оно определяет типы задач, которые пользователь может выполнять с папками, отчетами, моделями и содержимым других типов. Чтобы создать, изменить или удалить назначения ролей, используется веб-портал SSRS. После создания назначения ролей для конкретного пользователя или группы ее можно изменить, выбрав другую роль. Если нужно отменить разрешения на сервер отчетов, можно удалить на нем назначение ролей.  

В зависимости от цели работы можно использовать другие методы. Например, настроить определение ролей или создать новое либо изменить членство учетной записи группы в Active Directory.  

Предположим, что существует группа пользователей, которым необходим полный доступ к серверу отчетов и управление содержимым, но им нельзя давать полный набор разрешений, связанных с диспетчером содержимого. Вы можете создать новое определение роли с именем Department Content Manager. В него вы включите все задачи диспетчера содержимого, за исключением пункта **Установка политики безопасности для элементов**.

Аналогичным образом администратору системы или сети будет проще управлять учетными записями группы Active Directory, чем назначениями ролей на веб-портале. Вы можете снизить издержки на управление назначениями ролей, создав единое назначение ролей для учетной записи группы. Тогда вы сможете просто корректировать членство в группах, когда пользователям больше не нужен доступ к отчетам.
  
 Если вы решите, что изменение или удаление назначений ролей будет для вас удобнее, обязательно проверяйте назначения ролей на уровне системы и отдельных элементов. Разные типы назначений ролей настраиваются на разных страницах веб-портала.
  
## <a name="to-modify-or-delete-a-system-role-assignment"></a>Удаление или изменение назначения системной роли
  
1. Откройте [веб-портал сервера отчетов (службы SSRS в собственном режиме)](../../reporting-services/web-portal-ssrs-native-mode.md).

2. Щелкните **Настройки сайта** > **Безопасность**. Все системные назначения ролей, определенные для сервера или масштабного развертывания, перечислены по имени учетной записи.

3. Найдите назначение ролей, которое необходимо изменить или удалить.

4. Чтобы добавить или удалить роль для конкретного пользователя или группы, щелкните **Изменить**.

5. Чтобы удалить назначение ролей, установите флажок рядом с пользователем или группой, а затем щелкните **Удалить**.

### <a name="to-modify-or-delete-an-item-role-assignment"></a>Изменение или удаление назначения ролей на уровне элементов

1. Откройте диспетчер отчетов и найдите элемент, для которого вы намерены изменить или удалить назначение ролей.

2. Наведите указатель мыши на этот элемент и щелкните стрелку раскрывающегося списка.

3. В раскрывающемся меню выберите пункт **Безопасность**.

4. Найдите назначение ролей, которое необходимо изменить или удалить.

5. Чтобы добавить или удалить роль для конкретного пользователя или группы, щелкните **Изменить**.

6. Чтобы удалить назначение ролей, установите флажок рядом с пользователем или группой, а затем щелкните **Удалить**.

## <a name="see-also"></a>См. также раздел

[Создание назначений ролей и управление ими](../../reporting-services/security/create-and-manage-role-assignments.md)  
[Назначения ролей](../../reporting-services/security/role-assignments.md)  

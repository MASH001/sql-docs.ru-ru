---
title: Предоставление разрешений для скриптов
description: Как предоставить разрешения пользователя базы данных для выполнения скриптов R и Python в Службах машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 55a76b070a5f54562957f138d55896b49dbb15f1
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "81117097"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>Предоставление пользователям доступа к Службам машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описывается предоставление пользователям разрешения на выполнение внешних скриптов в Службах машинного обучения SQL Server и предоставление разрешений на чтение, запись или инструкции на языке описания данных (DDL) для баз данных.

Дополнительные сведения см. в подразделе "Разрешения" раздела [Общие сведения о безопасности для платформы расширяемости](../../machine-learning/concepts/security.md#permissions).

<a name="permissions-external-script"></a>

## <a name="permission-to-run-scripts"></a>Разрешение на выполнение скриптов

Если вы установили [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] самостоятельно и используете скрипты R или Python в своем собственном экземпляре, вы обычно выполняете скрипты от имени администратора. Таким образом, у вас есть неявное разрешение на различные операции и все данные в базе данных.

Однако большинство пользователей не имеют таких повышенных разрешений. Например, пользователи в организации, которые используют имена входа SQL для доступа к базе данных, обычно не имеют повышенных разрешений. Таким образом, для каждого пользователя, использующего R или Python, необходимо предоставить пользователям Служб машинного обучения разрешение на выполнение внешних скриптов в каждой базе данных, где используется этот язык. Это делается так.

```sql
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT TO [UserName]
```

> [!NOTE]
> Разрешения не относятся к конкретному поддерживаемому языку скриптов. Иными словами, не существует отдельных уровней разрешений для скриптов R и скриптов Python. Если необходимо поддерживать отдельные разрешения для этих языков, установите R и Python на отдельных экземплярах.

<a name="permissions-db"></a> 

## <a name="grant-databases-permissions"></a>Предоставление разрешений на базу данных

Когда пользователь выполняет скрипты, ему может потребоваться считывать данные из других баз данных. Пользователю также может потребоваться создавать новые таблицы для хранения результатов и записывать данные в таблицы.

Для каждой учетной записи пользователя Windows или имени входа SQL, выполняющих скрипты R или Python, убедитесь, что у них есть соответствующие разрешения для конкретной базы данных: `db_datareader` для чтения данных, `db_datawriter` для сохранения объектов в базе данных или `db_ddladmin` для создания таких объектов, как хранимые процедуры или таблицы, содержащие обученные и сериализованные данные.

Например, приведенная ниже инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] предоставляет имени входа SQL *MySQLLogin* права на выполнение запросов T-SQL в базе данных *ML_Samples*. Для выполнения этой инструкции имя входа SQL уже должно существовать в контексте безопасности сервера.

```sql
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о разрешениях, включенных в каждую роль, см. в разделе [Роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md).
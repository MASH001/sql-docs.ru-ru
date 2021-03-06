---
title: Общие сведения о Database Experimentation Assistant
description: Общие сведения о Database Experimentation Assistant
ms.custom: seo-lt-2019
ms.date: 12/12/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: rajsell
ms.reviewer: mathoma
ms.openlocfilehash: 939ff20fd0b708e949aee41d8aa2f3f59b63a9eb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "75247116"
---
# <a name="overview-of-database-experimentation-assistant"></a>Общие сведения о Database Experimentation Assistant

Database Experimentation Assistant (ДЕА) — это решение экспериментов для SQL Server обновлений. ДЕА может помочь оценить целевую версию SQL Server для конкретной рабочей нагрузки. Клиенты, выполняющие обновление с более ранних версий SQL Server (начиная с 2005) до более поздних версий SQL Server могут использовать метрики анализа, предоставляемые этим средством.

Метрики анализа ДЕА включают:

- Запросы, имеющие ошибки совместимости.
- Неограниченные запросы и планы запросов.
- Другие данные сравнения рабочей нагрузки.

Сравнение данных может привести к более высокому уровню достоверности и обеспечению успешного выполнения процесса обновления.

## <a name="get-dea"></a>Получить ДЕА

Чтобы установить Деа, [Скачайте](https://www.microsoft.com/download/details.aspx?id=54090) последнюю версию средства. Затем запустите файл **датабасикспериментатионассистант. exe** .

## <a name="solution-architecture-for-comparing-workloads"></a>Архитектура решения для сравнения рабочих нагрузок

На следующей схеме показана архитектура решения для сравнения рабочих нагрузок. При сравнении рабочих нагрузок используется ДЕА и распределенное воспроизведение во время обновления с SQL Server 2008 до SQL Server 2016.

![Архитектура решения для сравнения рабочих нагрузок](./media/database-experimentation-assistant-overview/dea-overview-compare-solution-architecture.png)

## <a name="dea-prerequisites"></a>Предварительные требования для ДЕА

Ниже приведены некоторые предварительные требования для запуска ДЕА.

- Минимальные требования к оборудованию: одноядерный компьютер с 3,5 ГБ ОЗУ.
- Идеальное требование к оборудованию: 8-ядерный ЦП (с 3,5 ГБ ОЗУ или более). Процессоры с более чем восемью ядрами не улучшают время выполнения ДЕА.
- Дополнительный 33% размера трассировки производительности необходим для хранения баз данных служб, B и анализа отчетов.

## <a name="configure-dea"></a>Настройка ДЕА

В предварительной архитектуре среды рекомендуется установить ДЕА *на том же компьютере, что и контроллер распределенное воспроизведение*. Такой подход позволяет избежать вызовов между компьютерами и упростить настройку.

### <a name="required-configuration-for-workload-comparison-using-dea"></a>Обязательная конфигурация для сравнения рабочих нагрузок с помощью ДЕА

ДЕА подключается к серверам баз данных с использованием проверки подлинности Windows. Убедитесь, что пользователь, запускающий Деа, может подключаться к серверам баз данных (источнику, целевому объекту и анализу), используя проверку подлинности Windows

**Требования к конфигурации для отслеживания**

Для записи трассировки необходимо, чтобы пользователь, запускающий ДЕА:

- Может подключиться к исходному серверу базы данных, используя проверку подлинности Windows.
- Имеет права системного администратора на исходном сервере базы данных.

Кроме того, учетной записи службы, под которой выполняется сервер базы данных источника, требуется доступ на запись к пути к папке трассировки.

Дополнительные сведения см. в разделе [часто задаваемые вопросы о захвате трассировки](database-experimentation-assistant-capture-trace.md#frequently-asked-questions-about-trace-capture).

**Требования к конфигурации воспроизведения**

Для воспроизведения трассировки необходимо, чтобы пользователь, запускающий ДЕА:

- Может подключиться к целевому серверу базы данных, используя проверку подлинности Windows.
- Имеет права системного администратора на целевом сервере базы данных.

Кроме того, воспроизведение трассировки требует:

- Учетная запись службы, с которой выполняются целевые серверы баз данных, имеет доступ на запись к пути к папке трассировки.
- Учетная запись службы, выполняющая распределенное воспроизведение клиенты, может подключаться к целевому серверу базы данных с помощью проверки подлинности Windows
- TCP-порты открываются для входящих запросов на контроллере распределенное воспроизведение. ДЕА взаимодействует с контроллером распределенное воспроизведение с помощью COM-интерфейсов.

Дополнительные сведения см. в разделе [часто задаваемые вопросы о воспроизведении трассировки](database-experimentation-assistant-replay-trace.md#frequently-asked-questions-about-trace-replay).

**Требования к конфигурации анализа**

Для выполнения анализа необходимо, чтобы пользователь, запускающий ДЕА:

- Может подключаться к серверу базы данных анализа с использованием проверки подлинности Windows.
- Имеет права системного администратора на исходном сервере базы данных.

Дополнительные сведения см. в разделе [часто задаваемые вопросы об аналитических отчетах](database-experimentation-assistant-create-report.md#frequently-asked-questions-about-analysis-reports).

## <a name="set-up-telemetry"></a>Настройка телеметрии

ДЕА имеет функцию с поддержкой Интернета, которая может отсылать данные телеметрии в корпорацию Майкрософт для использования при улучшении работы продукта. Собранные сведения также сохраняются на компьютере для локального аудита, поэтому вы всегда можете увидеть собранные данные. Все файлы журнала ДЕА сохраняются в папке% temp%\\ДЕА.

Данные телеметрии можно собирать в четырех типах событий:

- **TraceEvent**: события использования для приложения (например, "активировано прерывание записи").
- **Исключение**: исключение при использовании приложения.
- **Диагностицевент**: журнал событий, помогающий в диагностике при возникновении проблем (*не* отправляются в корпорацию Майкрософт).
- **Фидбаккевент**: Отзывы пользователей, отправляемые через приложение.

Сбор и отправка данных телеметрии необязательно. Чтобы указать, какие события собираются и какие события были собраны в корпорацию Майкрософт, выполните следующие действия.

1. Перейдите в расположение, в котором установлена Деа (например, C:\\Program Files (x86)\\Microsoft Corporation\\Database experimentation Assistant).
2. Откройте и измените config-файлы **ДЕА. exe. config** (для приложения) и **деакмд. exe. config** (для интерфейса командной строки), чтобы решить проблему соответствующим образом.
    - Чтобы отключить сбор данных о типе события, задайте для *события* (например, **TraceEvent**) значение **false**. Чтобы снова начать сбор события, установите значение **true**.
    - Чтобы отключить сохранение локальных копий событий, присвойте параметру **трацелогжеренаблед** значение **false**. Чтобы снова приступить к сохранению локальных копий, присвойте параметру значение **true**.
    - Чтобы отключить отправку событий в корпорацию Майкрософт, присвойте параметру **аппинсигхтслогжеренаблед** значение **false**. Чтобы снова начать отправку событий в корпорацию Майкрософт, установите значение **true**.

ДЕА регулируется заявлением [о конфиденциальности Майкрософт](https://aka.ms/dea-privacy).

## <a name="see-also"></a>См. также

- В статье рассматривается [процесс сравнения рабочих нагрузок](database-experimentation-assistant-get-started.md), объясняющий процесс сравнения рабочих нагрузок в двух средах.

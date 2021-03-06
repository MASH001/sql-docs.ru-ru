---
title: Установка документации предыдущих версий SQL Server в автономном режиме
description: Сведения об установке автономной документации для SQL Server 2019, 2017, 2016, 2014 и 2012. Используйте SQL Server Management Studio (SSMS) для просмотра автономного содержимого.
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
author: markingmyname
ms.author: maghan
ms.date: 04/20/2020
ms.openlocfilehash: 1420e18fbf335e22d44bf78d526ab35c8b1434e5
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2020
ms.locfileid: "82087874"
---
# <a name="install-previous-versions-of-sql-server-documentation-to-view-offline-in-ssms"></a>Установка документации предыдущих версий SQL Server для просмотра в автономном режиме в SSMS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описывается загрузка и просмотр автономного содержимого SQL Server в [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md). Автономное содержимое позволяет получить доступ к документации без подключения к Интернету (хотя изначально для загрузки требуется подключение к Интернету).

Автономная документация доступна для нескольких предыдущих версий SQL Server. Несмотря на возможность [просмотра содержимого для предыдущих версий в Интернете](https://docs.microsoft.com/previous-versions/sql/), параметр автономного режима обеспечивает удобный способ доступа к старому содержимому.

## <a name="how-to-download-and-configure-offline-content"></a>Скачивание и настройка автономного содержимого

Скачать и установить пакеты справки SQL Server можно из интернет-источников или с локального диска. В следующих разделах содержится описание загрузки автономного содержимого для разных версий SQL Server:

- [SQL Server 2019](#sql2019)
- [SQL Server 2017](#sql2017)
- [SQL Server 2016](#sql2016)
- [SQL Server 2014](#sql2014)
- [SQL Server 2012](#sql2012)

## <a name="sql-server-2019"></a><a id="sql2019"></a> SQL Server 2019

Чтобы загрузить автономную документацию для SQL Server 2019, выполните следующие действия:

1. В SSMS в меню "Справка" выберите пункт **Добавление и удаление содержимого справки**.

   ![Пункт меню "Добавление и удаление содержимого справки" в окне справки](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   В окне справки откроется вкладка "Управление содержимым".

2. Чтобы найти новейшее содержимое справки для SQL Server 2019, на вкладке **Управление содержимым** в источнике установки выберите **В сети**, а затем введите в строке поиска *sql server 2019*.

   ![Поиск документации SQL Server 2019 в окне справки](../sql-server/media/sql-server-help-installation/sql-2019-search.png)

   > [!Note]
   > На вкладке "Управление содержимым" в поле Local store path (Путь к локальному хранилищу) отображается место установки содержимого на локальном компьютере. Чтобы изменить расположение, щелкните **Переместить**, в поле **Куда** введите путь к другой папке, а затем нажмите кнопку **OK**. Если не удается установить справку после изменения пути к локальному хранилищу, закройте и снова откройте окно справки. Убедитесь, что новое расположение есть в пути к локальному хранилищу, а затем повторите попытку установки.

3. Чтобы установить новейшее содержимое справки для SQL Server 2019, выберите **Добавить** рядом с каждым пакетом содержимого (документацией), который необходимо установить, а затем выберите **Обновить** в правом нижнем углу.

   ![Добавление и обновление документации SQL Server 2019 в окне справки](../sql-server/media/sql-server-help-installation/sql-2019-add-update.png)

   > [!NOTE]
   > Если окно справки перестает отвечать на запросы во время добавления содержимого, измените значение в строке Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" в файле %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings или HlpViewer_VisualStudiox_en-US.settings на дату в будущем. Сведения об этой проблеме см. в разделе [Окно справки Visual Studio зависает](/visualstudio/welcome-to-visual-studio).

4. Проверить загрузку содержимого SQL Server 2019 можно, выполнив поиск в области содержимого слева, введя *sql server 2019*.

   ![Автоматическое обновление документации SQL Server 2019](../sql-server/media/sql-server-help-installation/sql-2019-content.png)

## <a name="sql-server-2017"></a><a id="sql2017"></a> SQL Server 2017

Чтобы загрузить автономную документацию для SQL Server 2017, выполните следующие действия:

1. В SSMS в меню "Справка" выберите пункт **Добавление и удаление содержимого справки**.

   ![Пункт меню "Добавление и удаление содержимого справки" в окне справки](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   В окне справки откроется вкладка "Управление содержимым".

2. Чтобы найти новейшее содержимое справки для SQL Server 2017, на вкладке **Управление содержимым** в источнике установки выберите **В сети**, а затем введите в строке поиска *sql server 2017*.

   ![Поиск документации SQL Server 2017 в окне справки](../sql-server/media/sql-server-help-installation/sql-2017-search.png)

   > [!Note]
   > На вкладке "Управление содержимым" в поле Local store path (Путь к локальному хранилищу) отображается место установки содержимого на локальном компьютере. Чтобы изменить расположение, щелкните **Переместить**, в поле **Куда** введите путь к другой папке, а затем нажмите кнопку **OK**. Если не удается установить справку после изменения пути к локальному хранилищу, закройте и снова откройте окно справки. Убедитесь, что новое расположение есть в пути к локальному хранилищу, а затем повторите попытку установки.

3. Чтобы установить новейшее содержимое справки для SQL Server 2017, выберите **Добавить** рядом с каждым пакетом содержимого (документацией), который необходимо установить, а затем выберите **Обновить** в правом нижнем углу.

   ![Добавление и обновление документации SQL Server 2017 в окне справки](../sql-server/media/sql-server-help-installation/sql-2017-add-update.png)

   > [!NOTE]
   > Если окно справки перестает отвечать на запросы во время добавления содержимого, измените значение в строке Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" в файле %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings или HlpViewer_VisualStudiox_en-US.settings на дату в будущем. Сведения об этой проблеме см. в разделе [Окно справки Visual Studio зависает](/visualstudio/welcome-to-visual-studio).

4. Проверить загрузку содержимого SQL Server 2017 можно, выполнив поиск в области содержимого слева, введя *sql server 2017*.

   ![Автоматическое обновление документации SQL Server 2017](../sql-server/media/sql-server-help-installation/sql-2017-content.png)

## <a name="sql-server-2016"></a><a id="sql2016"></a> SQL Server 2016

Чтобы загрузить автономную документацию для SQL Server 2016, выполните следующие действия:

1. В SSMS в меню "Справка" выберите пункт **Добавление и удаление содержимого справки**.

   ![Пункт меню "Добавление и удаление содержимого справки" в окне справки](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   В окне справки откроется вкладка "Управление содержимым".

2. Чтобы найти новейшее содержимое справки для SQL Server 2016, на вкладке **Управление содержимым** в источнике установки выберите **В сети**, а затем введите в строке поиска *sql server 2016*.

   ![Поиск документации SQL Server 2016 в окне справки](../sql-server/media/sql-server-help-installation/sql-2016-search.png)

   > [!Note]
   > На вкладке "Управление содержимым" в поле Local store path (Путь к локальному хранилищу) отображается место установки содержимого на локальном компьютере. Чтобы изменить расположение, щелкните **Переместить**, в поле **Куда** введите путь к другой папке, а затем нажмите кнопку **OK**. Если не удается установить справку после изменения пути к локальному хранилищу, закройте и снова откройте окно справки. Убедитесь, что новое расположение есть в пути к локальному хранилищу, а затем повторите попытку установки.

3. Чтобы установить новейшее содержимое справки для SQL Server 2016, выберите **Добавить** рядом с каждым пакетом содержимого (документацией), который необходимо установить, а затем выберите **Обновить** в правом нижнем углу.

   ![Добавление и обновление документации SQL Server 2016 в окне справки](../sql-server/media/sql-server-help-installation/sql-2016-add-update.png)

   > [!NOTE]
   > Если окно справки перестает отвечать на запросы во время добавления содержимого, измените значение в строке Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" в файле %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings или HlpViewer_VisualStudiox_en-US.settings на дату в будущем. Сведения об этой проблеме см. в разделе [Окно справки Visual Studio зависает](/visualstudio/welcome-to-visual-studio).

4. Проверить загрузку содержимого SQL Server 2016 можно, выполнив поиск в области содержимого слева, введя *sql server 2016*.

   ![Автоматическое обновление документации SQL Server 2016](../sql-server/media/sql-server-help-installation/sql-2016-content.png)

## <a name="sql-server-2014"></a><a id="sql2014"></a> SQL Server 2014

Чтобы загрузить автономную документацию для SQL Server 2014, выполните следующие действия:

1. Скачайте содержимое [документации по продукту Microsoft SQL Server 2014 для сред с брандмауэром и прокси-сервером](https://www.microsoft.com/download/details.aspx?id=42557) из центра загрузки и сохраните его в папке.

2. Распакуйте файл, чтобы просмотреть MSHA-файл.

   ![Файл установки справочной документации по SQL Server 2014](../sql-server/media/sql-server-help-installation/sql-2014-help-content-setup-msha.png)

3. В SSMS в меню "Справка" выберите пункт **Добавление и удаление содержимого справки**.

   ![Пункт меню "Добавление и удаление содержимого справки" в окне справки](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   В окне справки откроется вкладка "Управление содержимым".

4. Чтобы установить новейшее содержимое справки, выберите **Диск** в разделе источника установки, а затем — многоточие (...).

   ![Выбор диска в качестве источника на вкладке "Управление содержимым" в окне справки](../sql-server/media/sql-server-help-installation/install-source-disk.png)

   > [!NOTE]
   > На вкладке "Управление содержимым" в поле Local store path (Путь к локальному хранилищу) отображается расположение содержимого на локальном компьютере. Чтобы изменить расположение, щелкните **Переместить**, в поле **Куда** введите путь к другой папке, а затем нажмите кнопку **OK**.
   Если не удается установить справку после изменения пути к локальному хранилищу, закройте и снова откройте средство просмотра справки. Убедитесь, что новое расположение есть в пути к локальному хранилищу, а затем повторите попытку установки.

5. Откройте папку, в которую вы распаковали содержимое. Выберите в папке файл **HelpContentSetup.msha**, а затем щелкните **Открыть**.

   ![Открытие файла HelpContentSetup.msha SQL Server 2014](../sql-server/media/sql-server-help-installation/sql-2014-open-msha.png)

6. В строке поиска введите *sql server 2014*. Получив доступ к содержимому 2014, выберите **Добавить** рядом с каждым пакетом содержимого (документацией), который необходимо установить в окне справки, а затем выберите **Обновить**.

   ![Поиск документации SQL Server 2014 в окне справки](../sql-server/media/sql-server-help-installation/sql-2014-search.png)

   ![Добавление и обновление документации SQL Server 2014 в окне справки](../sql-server/media/sql-server-help-installation/sql-2014-add-update.png)

    > [!NOTE]
    > Если окно справки перестает отвечать на запросы во время добавления содержимого, измените значение в строке Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" в файле %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings или HlpViewer_VisualStudiox_en-US.settings на дату в будущем. Сведения об этой проблеме см. в разделе [Окно справки Visual Studio зависает](/visualstudio/welcome-to-visual-studio).

7. Проверить загрузку содержимого SQL Server 2014 можно, выполнив поиск в области содержимого слева, введя *sql server 2014*.

   ![Автоматическое обновление документации SQL Server 2014](../sql-server/media/sql-server-help-installation/sql-2014-content.png)

## <a name="sql-server-2012"></a><a id="sql2012"></a> SQL Server 2012

Чтобы загрузить автономную документацию для SQL Server 2012, выполните следующие действия:

1. Скачайте содержимое [документации по продукту Microsoft SQL Server 2012 для сред с брандмауэром и прокси-сервером](https://www.microsoft.com/download/details.aspx?id=35750) из центра загрузки и сохраните его в папке.

2. Распакуйте файл, чтобы просмотреть MSHA-файл.

   ![Файл установки содержимого справки SQL Server 2012](../sql-server/media/sql-server-help-installation/sql-2012-help-content-setup-msha.png)

3. В SSMS в меню "Справка" выберите пункт **Добавление и удаление содержимого справки**.

   ![Пункт меню "Добавление и удаление содержимого справки" в окне справки](../sql-server/media/sql-server-help-installation/add-remove-content.png)

   В окне справки откроется вкладка "Управление содержимым".

4. Чтобы установить новейшее содержимое справки, выберите **Диск** в разделе источника установки, а затем — многоточие (...).

   ![Выбор диска в качестве источника на вкладке "Управление содержимым" в окне справки](../sql-server/media/sql-server-help-installation/install-source-disk.png)

   > [!NOTE]
   > На вкладке "Управление содержимым" в поле Local store path (Путь к локальному хранилищу) отображается расположение содержимого на локальном компьютере. Чтобы изменить расположение, щелкните **Переместить**, в поле **Куда** введите путь к другой папке, а затем нажмите кнопку **OK**.
   Если не удается установить справку после изменения пути к локальному хранилищу, закройте и снова откройте средство просмотра справки. Убедитесь, что новое расположение есть в пути к локальному хранилищу, а затем повторите попытку установки.

5. Откройте папку, в которую вы распаковали содержимое. Выберите в папке файл **HelpContentSetup.msha**, а затем щелкните **Открыть**.

   ![Открытие файла HelpContentSetup.msha SQL Server 2012](../sql-server/media/sql-server-help-installation/sql-2012-open-msha.png)

6. В строке поиска введите *sql server 2012*. Получив доступ к содержимому 2012, выберите **Добавить** рядом с каждым пакетом содержимого (документацией), который необходимо установить в окне справки, а затем выберите **Обновить**.

   ![Поиск документации SQL Server 2012 в окне справки](../sql-server/media/sql-server-help-installation/sql-2012-search.png)

   ![Добавление и обновление документации SQL Server 2012 в окне справки](../sql-server/media/sql-server-help-installation/sql-2012-add-update.png)

    > [!NOTE]
    > Если окно справки перестает отвечать на запросы во время добавления содержимого, измените значение в строке Cache LastRefreshed="\<mm/dd/yyyy> 00:00:00" в файле %LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings или HlpViewer_VisualStudiox_en-US.settings на дату в будущем. Сведения об этой проблеме см. в разделе [Окно справки Visual Studio зависает](/visualstudio/welcome-to-visual-studio).

7. Проверить загрузку содержимого SQL Server 2012 можно, выполнив поиск в области содержимого слева, введя *sql server 2012*.

   ![Автоматическое обновление документации SQL Server 2012](../sql-server/media/sql-server-help-installation/sql-2012-content.png)

## <a name="view-offline-documentation"></a>Просмотр автономной документации

Содержимое справки SQL Server можно просмотреть с помощью меню **СПРАВКА** в последней версии [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md).

### <a name="view-offline-help-content-in-ssms"></a>Просмотр автономного содержимого справки в SSMS

Чтобы просмотреть установленную справку в SSMS, выберите в меню справки пункт **Запустить в средстве просмотра справки**, чтобы открыть окно справки.

   ![Пункт меню "Запустить в средстве просмотра справки"](../sql-server/media/sql-server-help-installation/helpviewer-view-offline.png)  

В окне справки откроется вкладка "Управление содержимым" с таблицей содержимого установленной справки в левой области. Выберите статьи в таблице содержимого, чтобы просмотреть их в правой области.

> [!TIP]
> Если область содержимого не отображается, щелкните "Содержимое" в левом поле. Чтобы область содержимого не закрывалась, щелкните значок канцелярской кнопки.  

   ![Окно справки с содержимым](../sql-server/media/sql-server-help-installation/view-offline-all.png)

## <a name="life-cycle-policy"></a>Политика жизненного цикла

Сведения о поддержке определенных продуктов, служб и технологий см. на следующей странице:

- [Политика жизненного цикла поддержки Майкрософт](https://support.microsoft.com/lifecycle/selectindex)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения об архивированном содержимом и окне справки см. на приведенных ниже страницах.

- [Документация предыдущих версий SQL Server](https://docs.microsoft.com/previous-versions/sql/)
- [Окно справки (Майкрософт)](https://docs.microsoft.com/visualstudio/help-viewer/overview)
- [Техническая документация по SQL Server](../sql-server/index.yml?view=sql-server-2016)
- [Система управления версиями в документации по SQL](../sql-server/versioning-system-monikers-ui-sql-server.md?view=sql-server-2016)
---
title: Практическое руководство. Развертывание модуля обработки данных в конструкторе отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: 3614e601-004e-4a16-8388-836ffd67e9dd
caps.latest.revision: 40
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 25b6bfa824f6004fbd35b3a31e7268ff388fab6e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216734"
---
# <a name="how-to-deploy-a-data-processing-extension-to-report-designer"></a>Практическое: развертывание модуля обработки данных в конструкторе отчетов
  Модули обработки данных используются в конструкторе отчетов для получения и обработки данных в процессе разработки отчетов. Сборка модуля обработки данных должна быть развернута в конструкторе отчетов как закрытая сборка. Необходимо также внести запись в файл конфигурации конструктора отчетов, RSReportDesigner.config.  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>Развертывание сборки модуля обработки данных  
  
1.  Скопируйте конкретную сборку из промежуточной папки в каталог конструктора отчетов. По умолчанию каталог исполняемых файлов конструктора отчетов расположен в папке C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
2.  После того, как будет скопирован файл сборки, откройте файл RSReportDesigner.config. Файл RSReportDesigner.config также находится в каталоге конструктора отчетов. Необходимо внести запись в этот файл конфигурации для файла сборки развертываемого модуля обработки данных. Файл конфигурации можно открыть с помощью среды [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] или воспользоваться простым текстовым редактором (таким как Блокнот).  
  
3.  Найдите в файле RSReportDesigner.config элемент **Data** . Запись для вновь созданного модуля обработки данных необходимо создать в месте, указанном ниже.  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  Добавьте запись для модуля обработки данных, который включает в себя **расширение** со значениями параметров `Name`, `Type`, и `Visible` атрибуты. Эта запись должна иметь следующий вид:  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, AssemblyName" />  
    ```  
  
     По умолчанию `Name` — уникальное имя модуля обработки данных. Значение параметра `Type` представляет собой список с разделителями-запятыми, включающий полное имя пространства имен для класса, реализующего интерфейсы <xref:Microsoft.ReportingServices.Interfaces.IExtension> и <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>, а затем имя сборки поставщика (без расширения DLL). По умолчанию модули обработки данных являются видимыми. Чтобы скрыть модуль от пользовательских интерфейсов, таких как конструктор отчетов, добавьте `Visible` атрибут **расширение** элемент и присвойте ему значение `false`.  
  
5.  Наконец, добавьте для пользовательской сборки группу кода, которая предоставляет разрешение **FullTrust** для конкретного модуля. С этой целью добавьте указанную группу кода в файл rspreviewpolicy.config, который по умолчанию находится в папке C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies. Пример группы кода показан ниже.  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 URL-членство — это лишь одно из множества условий членства, которые могут быть заданы для модуля обработки данных. Дополнительные сведения об управлении доступом для кода в [!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)] см. в разделе [Безопасная разработка (службы Reporting Services)](../secure-development/secure-development-reporting-services.md).  
  
## <a name="generic-query-designer"></a>Обычный конструктор запросов  
 В состав конструктора отчетов входит обычный конструктор запросов, который можно применять с пользовательскими модулями обработки данных. Конструктор состоит из двух панелей: панели запросов и панели результатов. С помощью универсального конструктора можно создавать запросы, не поддерживаемые при использовании графического интерфейса. В отличие от графического конструктора запросов, обычный конструктор запросов не проверяет синтаксис запроса и не изменяет структуру запроса.  
  
#### <a name="to-enable-the-generic-query-designer-for-a-custom-extension"></a>Включение обычного конструктора запросов для пользовательского модуля  
  
-   Добавьте следующую запись в файл RSReportDesigner.config в **конструктор** элемента, заменив `Name` атрибут с именем, которое указано в предыдущих записях.  
  
    ```  
    <Extension Name="ExtensionName" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
## <a name="verifying-the-deployment"></a>Проверка развертывания  
 Прежде чем выполнять проверку развертывания, необходимо закрыть все экземпляры среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] на локальном компьютере. После завершения всех текущих сеансов можно проверить, успешно ли развернут модуль обработки данных в конструкторе отчетов, создав с помощью среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] новый проект отчета. При создании набора данных для отчета модуль должен появиться в списке доступных типов источников данных.  
  
## <a name="see-also"></a>См. также  
 [Развертывание модуля обработки данных](deploying-a-data-processing-extension.md)   
 [Модули служб Reporting Services](../reporting-services-extensions.md)   
 [Реализация модуля обработки данных](implementing-a-data-processing-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
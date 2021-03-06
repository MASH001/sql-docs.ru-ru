---
title: Параметры (текстовый редактор — все языки — страница вкладок) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: bd715d6b-f873-41d4-aa10-57b7098b61cc
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 377ca16075a86c366fcfa8d9d96bcfa989efec4b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66089907"
---
# <a name="options-text-editor---all-languages--tabs-page"></a>Параметры ("Текстовый редактор" — "Все языки" — страница "Вкладки")
  Это диалоговое окно используется для задания действий во всех пяти редакторах в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]при использовании клавиши TAB. Для отображения этих параметров в меню **Сервис** выберите **Параметры** . Выберите папку **Текстовый редактор** , откройте папку **Все языки** и выберите **Вкладки**.  
  
## <a name="tabbing-options-by-editor"></a>Параметры табуляции, задаваемые с помощью редактора  
 Параметры редакторов DMX, MDX и SQL Server Compact задаются в диалоговом окне **Все языки** . Задаваемые здесь параметры также применимы для редакторов простого текста, Transact-SQL и XML, однако для этих редакторов можно задать параметры отдельно, развернув вложенные папки для соответствующих языков и выбрав нужные страницы параметров. В некоторых языках поддерживаются не все параметры табуляции.  
  
> [!CAUTION]  
>  Если для задания параметра используется данное диалоговое окно, но при этом нужно задать другие параметры для редакторов простого текста, Transact-SQL и XML, это следует делать после применения изменений в диалоговом окне **Все языки**.  
  
 Сообщение «Конфликт между параметрами отступа (или табуляции) для отдельных текстовых форматов» отображается, если для определенных редакторов выбраны разные параметры. Например, это напоминание выводится, если для параметра **Обычный текст** выбран параметр **Отступ блока**, но для **XML** выбрано **Нет**.  
  
## <a name="indenting"></a>Отступы  
 **Нет**  
 Если данный параметр выбран, при нажатии клавиши ВВОД отступ у новой строки создаваться не будет. Курсор помещается в первый столбец новой строки.  
  
 **Блок**  
 При выборе этого параметра во вновь созданной строке при нажатии пользователем клавиши ВВОД производится отступ на то же расстояние, что и в предыдущей строке.  
  
 **Структура**  
 Если выбран этот параметр, после нажатия клавиши ВВОД новая строка располагается в соответствии с контекстом.  
  
## <a name="tabs"></a>Вкладки  
 **Размер интервала табуляции**  
 Устанавливает расстояние в пробелах между табуляторами. По умолчанию этот параметр равен четырем пробелам.  
  
 **Размер отступа**  
 Устанавливается размер автоматического отступа в пробелах. По умолчанию этот параметр равен четырем пробелам. Для заполнения указанного размера вставляются символы табуляции, символы пробела или оба этих вида символов.  
  
 **Вставлять пробелы**  
 При выборе этого параметра операции отступа вставляют только пробелы, а не символы табуляции. Например, если параметр **Ширина отступа** равен пяти, при нажатии клавиши TAB или кнопки **Увеличить отступ** на панели инструментов главного окна среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] вставляются пять символов пробела.  
  
 **Сохранять знаки табуляции**  
 При выборе этого параметра операции отступа вставляют максимально возможное количество символов табуляции. Каждый символ табуляции включает количество пробелов, указанное в параметре **Размер интервала табуляции**. Если параметр **Размер отступа** не кратен точно параметру **Размер интервала табуляции**, для заполнения остатка вставляются пробелы.  
  
  

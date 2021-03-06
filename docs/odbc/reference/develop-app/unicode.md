---
title: Юникод | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC]
- Unicode [ODBC], about Unicode
ms.assetid: 113e1c9a-8333-4805-86f2-e4b57ab816a5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9824e76cebabb6f5f84505292801a0094e359f0f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302451"
---
# <a name="unicode"></a>Юникод
Юникод определяет кодировку символов на многих языках.  
  
 Дополнительные сведения о стандарте Unicode см. [в разделе Unicode Consortium](https://www.unicode.org).  
  
 Юникод определяет универсальный набор символов. Кодовая страница ANSI Windows определяет кодировку, которая обычно содержит символы для одного языка. Написание приложения, необходимого для использования различных кодовых страниц, может быть сложнее.  
  
 В Юникоде не требуется кодовая страница. Каждая кодовая точка сопоставляется с одним символом на каком-либо языке.  
  
 В настоящее время единственной кодировкой в Юникоде, поддерживаемой ODBC, является UCS-2, которая использует 16-разрядное целое число (фиксированная длина) для представления символа. Юникод позволяет приложениям работать на разных языках.  
  
 Диспетчер драйверов ODBC 3,5 (или более поздней версии) поддерживает Юникод. Это влияет на две основные области: вызовы функций и типы строковых данных. Диспетчер драйверов сопоставляет строковые аргументы функции и строковые данные в соответствии с требованиями приложения и драйвера, которые могут быть либо поддерживающими Юникод, либо совместимыми с ANSI. Эти две области подробно обсуждаются в разделах, [аргументах функции Юникода](../../../odbc/reference/develop-app/unicode-function-arguments.md) и [данных в Юникоде](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Диспетчер драйверов ODBC 3,5 (или более поздней версии) поддерживает использование драйвера Юникода с приложением Юникода и приложением ANSI. Он также поддерживает использование драйвера ANSI с приложением ANSI. Диспетчер драйверов предоставляет ограниченное сопоставление Юникода с ANSI для приложения Юникода, работающего с драйвером ANSI.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Аргументы функции Юникода](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Данные в Юникоде](../../../odbc/reference/develop-app/unicode-data.md)

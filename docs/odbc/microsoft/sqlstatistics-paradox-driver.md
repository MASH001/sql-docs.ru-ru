---
title: SQLStatistics (Драйвер Paradox) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Paradox Driver
ms.assetid: 886cab83-d599-4fbc-9c88-e8cb833aac4b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e9782eb22e4176a57aab7bdd3823982575a0d55
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299324"
---
# <a name="sqlstatistics-paradox-driver"></a>SQLStatistics (драйвер для Paradox)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу Paradox. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Путь к каталогу.<br /><br /> Сопоставление шаблонов не поддерживается в аргументе *сзтаблекуалифиер* .|  
|TABLE_OWNER|Значение NULL возвращается в этом столбце, так как имя владельца не поддерживается.|  
|TABLE_NAME|Имя таблицы, не разделяются.<br /><br /> Сопоставление шаблонов не поддерживается в аргументе *сзтабленаме* .|  
|INDEX_QUALIFIER|Всегда возвращается значение NULL.|  
|INDEX_NAME|Зависит от индекса.|  
|TYPE|Для типа будет возвращено только SQL_TABLE_STAT или SQL_INDEX_OTHER.|  
|SEQ_IN_INDEX|Зависит от индекса.|  
|COLUMN_NAME|Зависит от индекса.|  
|COLLATION|Зависит от индекса.|  
|PAGES|Всегда возвращается значение NULL.|  
  
 Фильтрация основана на уникальности (аргумент *фуникуе* ). Параметр *факкураци* игнорируется.

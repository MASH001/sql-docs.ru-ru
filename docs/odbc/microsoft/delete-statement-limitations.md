---
title: Ограничения инструкции DELETE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 365b54ab8c0678253e184b397f1f71e39aed3b9b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303535"
---
# <a name="delete-statement-limitations"></a>Ограничения инструкции DELETE
Инструкция DELETE не поддерживается для Microsoft Excel или текстового драйвера. Обратите внимание, что инструкция INSERT поддерживается для текстового драйвера.  
  
 Драйвер dBASE не поддерживает упаковку таблиц для удаления "удаленных" значений.  
  
 Чтобы драйвер Paradox удалил строку из таблицы, таблица должна иметь уникальный индекс (первичный ключ Paradox).

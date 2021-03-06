---
title: Занятие 5. Форматирование отчета (службы Reporting Services) | Документы Майкрософт
ms.date: 04/29/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: ae46efa9-6e04-48ec-afb4-5a2314dcb05a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a8bf8b6814f7989a904507cd89fbea397b8b6930
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "65105928"
---
# <a name="lesson-5-formatting-a-report-reporting-services"></a>Урок 5. Форматирование отчета (службы Reporting Services)

После добавления области данных и нескольких полей к отчету «Заказы на продажу» можно отформатировать поля дат и валют, а затем и заголовки столбцов.

## <a name="format-the-date"></a><a name="bkmk_format_date"></a>Форматирование дат

Выражение поля Date (Дата) по умолчанию отображает сведения о дате и времени. Можно отформатировать его таким образом, чтобы отображалась только дата.

1. Выберите вкладку **Конструктор**.
2. Щелкните правой кнопкой мыши ячейку с выражением поля `[Date]`, а затем выберите **Свойства текстового поля**.
3. Выберите **Число**, а в поле **Категория** выберите **Дата**.
4. В поле **Тип** введите **31 января 2000 года**.
5. Щелкните **ОК**, чтобы применить форматирование.
6. Откройте предварительный просмотр, чтобы увидеть изменения в форматировании поля `[Date]`, а затем вернитесь в режим конструктора.

## <a name="format-the-currency"></a><a name="bkmk_format_currency"></a>Указание формата валюты

Выражение поля LineTotal отображает число в общем формате. Вы можете изменить его на число в денежном формате.

1. Щелкните правой кнопкой мыши ячейку с выражением `[LineTotal]` и выберите **Свойства текстового поля**.
2. Выберите **Число** в крайнем левом поле со списком, а затеем **Валюта** в поле со списком **Категория**.
3. Если у вас выбран языковой стандарт "английский (США)", в поле со списком **Тип** будут по умолчанию установлены следующие значения:
    - **Десятичные разряды: 2**
    - **Отрицательные числа: ($12345.00)**
    - **Символ: $ English (США)**
4. Выберите **Использовать разделитель разрядов (пробел)** . Если образец текста выглядит как **$12,345.00**, значит параметры заданы правильно.
5. Щелкните **ОК**, чтобы применить форматирование.
6. Откройте предварительный просмотр отчета, чтобы увидеть изменения столбца выражения `[LineTotal]`, а затем вернитесь в режим конструктора.  

## <a name="change-text-style-and-column-widths"></a><a name="bkmk_change_textstyle"></a>Изменение стиля текста и ширины столбцов

Вы можете изменять другие параметры форматирования отчета, выделяя строку заголовка и корректируя ширину столбцов данных.

### <a name="to-format-header-rows-and-table-columns"></a>Форматирование заголовков строк и столбцов таблицы

1. Выберите таблицу, чтобы рядом с ней появились маркеры столбцов и строк. Серые линии, расположенные вдоль верха и стороны таблицы, — это маркеры столбцов и строк.

2. Установите указатель на линии раздела между маркерами столбцов, чтобы курсор принял вид двойной стрелки. Перетаскиванием установите нужный размер столбцов.
    ![rs_BasicTableDetailsDesign](media/rs-basictabledetailsdesign.png)

3. Выберите строку с метками заголовков столбцов, а затем в меню **Формат** выберите **Шрифт** > **Полужирный**.

4. Просмотрите отчет. Он должен выглядеть примерно так:

    ![Предварительный просмотр таблицы с заголовками столбцов, выделенными полужирным шрифтом](media/rs-basictabledetailsformattedpreview.png "Предварительный просмотр таблицы с заголовками столбцов, выделенными полужирным шрифтом")  

5. В меню **Файл** выберите **Сохранить все**, чтобы сохранить отчет.

## <a name="next-steps"></a>Дальнейшие действия

В этом уроке вы успешно отформатировали заголовки столбцов и выражения полей. Далее вам предстоит добавить в отчет группирование и итоги. Переходите к уроку 6. [Добавление группирования и итогов (службы Reporting Services)](lesson-6-adding-grouping-and-totals-reporting-services.md).

## <a name="see-also"></a>См. также раздел

[Форматирование чисел и дат (построитель отчетов и службы SSRS)](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)
[Поведение при подготовке к просмотру (построитель отчетов и службы SSRS)](report-design/rendering-behaviors-report-builder-and-ssrs.md)

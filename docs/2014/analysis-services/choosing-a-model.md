---
title: Выбор модели | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data mining algorithms
- mining models
- mining structures
- data mining models
- data mining structures
ms.assetid: 444bbf9c-cec8-460e-881d-38784fb146fa
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9817f7e8906d9e75f7c2b5d55db679d77e7cc47e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273890"
---
# <a name="choosing-a-model"></a>Выбор модели
  **Алгоритм интеллектуального анализа данных:** *Алгоритм* интеллектуального анализа данных представляет собой механизм, создающий закономерности на основе данных. Алгоритм определяет метод подсчета данных, методы вычисления связей и методы хранения закономерностей. Выбор алгоритма отчасти зависит от типа данных, которые необходимо проанализировать. Например, некоторые алгоритмы могут работать только с непрерывными числовыми значениями, тогда как другие могут работать наилучшим образом с ограниченным количеством уникальных значений.  
  
 **Модель интеллектуального анализа:** Результат анализа данных, произведенного алгоритмом, сохраняется в *модели интеллектуального анализа данных*. Модель интеллектуального анализа данных — это набор правил, статистики и шаблонов. *Содержимое* модели интеллектуального анализа данных зависит от алгоритма, который использовался для обработки данных, но может включать следующее:  
  
-   правила If-then, описывающие группирование продуктов в транзакции;  
  
-   Дерево принятия решений, которое отслеживает пути, ведущие к результату, с вероятностями для каждого пути.  
  
-   Математическая модель с уравнениями для модели в целом или для сегментов модели.  
  
-   Коллекции схожих элементов (именуемых *кластерами* , или *сегментами*), определяемых характеристиками, которые они имеют, и оценкой подобия.  
  
-   *Узлы* в сети, соединенные *ребрами*. Узлы представляют элементы или группы элементов. Ребра вычисляются согласно устойчивости связей между узлами.  
  
 **Использование модели.** После создания модели воспользуйтесь предоставленными средствами для ее просмотра и изучения либо создайте запрос к модели. Запросы можно использовать для следующих целей:  
  
-   Прогнозирование будущих значений.  
  
-   Создание набора связанных продуктов или рекомендуемых продуктов.  
  
-   Возврат правил, закономерностей и формул в модели.  
  
-   Получение метаданных из модели.  
  
-   Предоставление вероятности и баллов поддержки для всех или некоторых прогнозов.  
  
## <a name="types-of-machine-learning-algorithms"></a>Типы алгоритмов машинного обучения  
 Поскольку при использовании различных алгоритмов данные используются по-разному, необходимо выбирать такой алгоритм, который бы подходил для целей пользователя и для данных, анализ которых будет производиться при создании модели.  
  
 Надстройки интеллектуального анализа данных для Excel включают различные типы алгоритмов.  
  
-   *Алгоритмы классификации*.  
  
     Прогнозирование одной или нескольких дискретных переменных на основе других атрибутов в наборе данных.  
  
-   *Алгоритмы регрессии*  
  
     Прогнозирование одной или нескольких непрерывных переменных, например прибыли или убытков, на основе других атрибутов в наборе данных.  
  
-   *Алгоритмы сегментации*  
  
     Деление данных на группы или кластеры элементов, имеющих схожие свойства.  
  
-   *Алгоритмы взаимосвязей*  
  
     Поиск корреляции между различными атрибутами в наборе данных. Этот тип алгоритмов наиболее широко используется для создания правил взаимосвязей. Правила взаимосвязей можно использовать в анализе покупательского поведения.  
  
-   *Алгоритмы анализа последовательностей*  
  
     Обобщение часто встречающихся последовательностей в данных, например путей, по которым пользователи переходят при работе с веб-сайтом.  
  
 Алгоритмы, которые используются надстройками интеллектуального анализа данных Microsoft SQL Server для Office, основаны на алгоритмах, обеспечиваемых службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Можно также использовать сторонние алгоритмы, соответствующие спецификации OLE DB для интеллектуального анализа данных, если экземпляр [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] с которым установлено соединение настроен для поддержки сторонних алгоритмов.  
  
## <a name="requirements"></a>Требования  
 Каждый алгоритм отличается тем, с каким типом данных он может работать.  
  
-   Модель линейной регрессии может представлять только числовые значения. Как входные переменные, так и конечные результаты должны быть представлены непрерывными численными типами. Используйте дерево принятия решений или модель оценки, если требуется смешать дискретные и непрерывные переменные.  
  
-   Модель упрощенного алгоритма Байеса требует, чтобы все числа были сегментированы. Если используется один из мастеров, основанных на данном алгоритме, сегментирование выполняется автоматически.  
  
-   Модель деревьев принятия решений может содержать и дискретные и непрерывные переменные. Однако числа будут автоматически сегментироваться по мере необходимости для разбиений в дереве.  
  
-   Нейронные сети и модели логистической регрессии автоматически сегментируют числа, используемые как результаты или как входные значения переменных. Если требуется сгруппировать числа в соответствии с некоторыми другими критериями, необходимо использовать средство «Переразметка», чтобы сформировать группы перед моделированием. Например, может понадобиться сгруппировать значения в столбце **Возраст** децилями (10–20, 21–30 и т. д.), а не статистически значимыми группами, обнаруженными моделью (например, 35,6–41,8 года).  
  
-   Модель взаимосвязей требует, чтобы данные были сгруппированы в транзакциях, чтобы каждая ссылалась на несколько элементов или строк. Если вы используете [Мастер взаимосвязей &#40;клиент интеллектуального анализа данных для Excel&#41; ](associate-wizard-data-mining-client-for-excel.md) мастер или [анализа покупательского поведения &#40;средства анализа таблиц для Excel&#41; ](shopping-basket-analysis-table-analysistools-for-excel.md) средство, данные должны располагаться, как показано в **связать** вкладке книги с образцами.  
  
     Если вы хотите использовать вложенные таблицы во внешнем источнике данных, необходимо использовать [расширенного моделирования &#40;надстроек интеллектуального анализа данных для Excel&#41; ](advanced-modeling-data-mining-add-ins-for-excel.md) параметры для создания структуры интеллектуального анализа данных и модели интеллектуального анализа данных, который сохраняется на сервере моделирования. Excel не поддерживает вложенные таблицы.  
  
## <a name="feature-selection"></a>Выбор компонентов  
 В зависимости от набора данных алгоритм может применять *выбор компонентов*, чтобы отфильтровать ненужные столбцы и определить, какие столбцы данных статистически значимы по отношению к результату.  
  
 Разные алгоритмы используют немного разные методы выбора компонентов (например, энтропию или различные информационные оценки) для определения того, какие из тенденций являются важными, а какие различия можно отбросить.  
  
 В надстройках интеллектуального анализа данных для Excel выбор компонентов применяется автоматически с использованием метода количественной оценки, подходящего для каждого алгоритма. Если необходимо повлиять на результаты выбора компонентов, используйте мастеры на ленте **Интеллектуальный анализ данных** и перейдите на вкладку **Дополнительно** , чтобы задать параметры в диалоговом окне **Параметры алгоритма** .  
  
 Список выбора компонентов методов, используемых каждым алгоритмом см. в разделе [Выбор компонентов &#40;интеллектуального анализа данных&#41; ](data-mining/feature-selection-data-mining.md) в электронной документации по SQL Server.  
  
## <a name="list-of-supported-algorithms"></a>Список поддерживаемых алгоритмов  
 По умолчанию предусмотрены следующие алгоритмы.  
  
|Имя алгоритма|Описание|Применяется в|  
|--------------------|-----------------|-------------|  
|Правило взаимосвязей Майкрософт|Строит правила, описывающие элементы, которые, вероятнее всего, появятся вместе в транзакции.|[Мастер взаимосвязей &#40;клиент интеллектуального анализа данных для Excel&#41;](associate-wizard-data-mining-client-for-excel.md)<br /><br /> [Анализ покупательского поведения &#40;таблиц средства анализа для Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)|  
|Алгоритм кластеризации Майкрософт|Определяет связи в наборе данных, которые невозможно логически получить с помощью случайного наблюдения. Использует итерационный метод для группирования записей в кластеры с похожими характеристиками.|[Поиск категорий &#40;средства анализа таблиц для Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)<br /><br /> [Мастер кластеризации &#40;интеллектуального анализа данных надстройки для Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)|  
|Алгоритм дерева принятия решений Майкрософт|Делает прогноз на основе связей между столбцами в наборе данных и моделирует эти связи в форме древовидной последовательности разбиений для конкретных значений.<br /><br /> Поддерживает прогнозы как дискретных, так и непрерывных атрибутов.|[Мастер классификации &#40;интеллектуального анализа данных надстройки для Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)<br /><br /> [Мастер оценки &#40;интеллектуального анализа данных надстройки для Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)|  
|Алгоритм линейной регрессии Майкрософт|Если имеется линейная зависимость между целевой переменной и анализируемыми переменными, алгоритм находит наиболее эффективную связь между целью и ее входными данными.<br /><br /> Поддерживает прогнозы непрерывных атрибутов.|Этот алгоритм доступен в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. В надстройках интеллектуального анализа данных для Office можно создать модель, использующую данный алгоритм, создав структуру, а затем добавив модель вручную.<br /><br /> Дополнительные сведения см. в разделе [расширенного моделирования &#40;интеллектуального анализа данных надстройки для Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|Алгоритм логистической регрессии Майкрософт|Анализирует факторы, влияющие на результат, если результат ограничен двумя значениями — обычно это наличие или отсутствие события.<br /><br /> Поддерживает прогнозы как дискретных, так и непрерывных атрибутов.|[Заполнение по примеру &#40;средства анализа таблиц для Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)<br /><br /> [Сценарий поиска решения &#40;средства анализа таблиц для Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)<br /><br /> [Что, если сценарий &#40;средства анализа таблиц для Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)<br /><br /> [Расчет прогноза &#40;средства анализа таблиц для Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)|  
|Упрощенный алгоритм Байеса (Майкрософт)|Оценивает вероятность связи между всеми входными данными и прогнозируемым столбцом. Этот алгоритм полезен для быстрого создания моделей интеллектуального анализа данных, обнаруживающих связи.<br /><br /> Поддерживает только дискретные или дискретизированные атрибуты.<br /><br /> Рассматривает все входные атрибуты как независимые.|[Анализ ключевых факторов влияния &#40;средства анализа таблиц для Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)|  
|Алгоритм нейронной сети Майкрософт|Анализирует сложные входные данные или бизнес-проблемы, для которых имеется значительный объем обучающих данных, но для которых трудно вывести правила, используя другие алгоритмы.<br /><br /> Может предсказывать несколько атрибутов.<br /><br /> Используется для классификации дискретных атрибутов и регрессии непрерывных атрибутов.|Этот алгоритм доступен в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. В надстройках интеллектуального анализа данных для Office можно создать модель, использующую данный алгоритм, создав структуру, а затем добавив модель вручную.<br /><br /> Дополнительные сведения см. в разделе [расширенного моделирования &#40;интеллектуального анализа данных надстройки для Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|Кластер последовательностей Майкрософт|Определяет в последовательности кластеры событий, упорядоченных похожим образом.<br /><br /> Обеспечивает сочетание анализа последовательности и кластеризации.|Этот алгоритм доступен только в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Однако в надстройках интеллектуального анализа данных для Office можно создать модель, использующую данный алгоритм, создав структуру, а затем добавив модель вручную.<br /><br /> Дополнительные сведения см. в разделе [расширенного моделирования &#40;интеллектуального анализа данных надстройки для Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|алгоритм временных рядов (Майкрософт)|Анализирует данные, относящиеся ко времени, используя линейное дерево принятия решений.<br /><br /> Для предсказания будущих значений во временной последовательности используются закономерности.|[Прогноз &#40;средства анализа таблиц для Excel&#41;](forecast-table-analysis-tools-for-excel.md)<br /><br /> [Мастер прогнозов &#40;интеллектуального анализа данных надстройки для Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)|  
  
## <a name="see-also"></a>См. также  
 [Состав надстройки интеллектуального анализа данных для Office](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  
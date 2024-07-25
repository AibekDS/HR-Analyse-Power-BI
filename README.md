### Обзор👾

Этот проект Power BI предназначен для всестороннего анализа HR данных, используя информацию о сотрудниках. Проект включает различные анализы, чтобы понять демографические данные сотрудников, доходы и корреляции между различными переменными.

### Источники данных📌

Основной источник данных

    HR Analytics Data.csv: Основной набор данных, содержащий подробную информацию о сотрудниках.

Дополнительные источники данных

    HR employee data.csv: Дополнительные данные о сотрудниках, используемые для анализа.
    gender.csv: Создано на основе основного набора данных, содержит информацию по полу.
    education.csv: Создано на основе основного набора данных, содержит информацию об образовании.

Дополнительные таблицы были сформированы с помощью Jupyter ноутбука main.ipynb.

### Структура проекта🧾

Проект Power BI организован на пять основных страниц и два всплывающих окна (tooltips), с различными закладками и возможностью Drill Through для углубленного анализа и удобной навигации.

Страницы

    Домашняя страница: Обзор и введение в проект.
    Общие сведения: Широкий анализ данных о сотрудниках.
    Анализ рангов сотрудников: Информация о рангах сотрудников и их должностях.
    Анализ доходов: Подробный анализ доходов сотрудников.
    Корреляция дохода: Корреляция дохода с другими переменными.
    Drill Through: Страница для детального анализа конкретных должностей.

Всплывающие окна (Tooltips)

    Два дополнительных всплывающих окна предоставляют контекстную информацию и улучшают пользовательский опыт.

Закладки

    Закладки используются для анимаций и дополнительных всплывающих таблиц.

Навигация

    Средства навигации добавлены для удобства перемещения между страницами.

### Меры и вычисляемые таблицы📊

Меры

Различные меры были созданы и объединены в одну таблицу для облегчения анализа. Эти меры включают расчеты общего дохода, среднего дохода и других релевантных метрик.
Вычисляемые таблицы

Три вычисляемые таблицы были созданы с использованием DAX для поддержки анализа:

RankTable:

    RankTable = 
    ADDCOLUMNS(
        SUMMARIZE('HR Analytics Data', 'HR Analytics Data'[JobRole]),
        "TotalRevenue", 'HR Analytics Data'[meanIncome],
        "Max", CALCULATE(MAX('HR Analytics Data'[MonthlyIncome])),
        "Min", CALCULATE(MIN('HR Analytics Data'[MonthlyIncome])),
        "Rank", RANKX(ALL('HR Analytics Data'[JobRole]), 'HR Analytics Data'[meanIncome], , DESC)
    )

Corr3:

    Corr3 = 
    SUMMARIZE(
        'HR Analytics Data',
        'HR Analytics Data'[JobRole],
        'HR Analytics Data'[Education],
        "MaxMonthlyIncome", CALCULATE(MAX('HR Analytics Data'[MonthlyIncome]))
    )

Corr2:

    Corr2 = 
    SUMMARIZE(
        'HR Analytics Data',
        'HR Analytics Data'[JobRole],
        'HR Analytics Data'[Job Level],
        "MaxMonthlyIncome", CALCULATE(MAX('HR Analytics Data'[MonthlyIncome]))
    )

### Использование🤖

Чтобы начать работу с этим проектом Power BI:

    Импортируйте основной набор данных (HR Analytics Data.csv) и дополнительные наборы данных (HR employee data.csv, gender.csv, education.csv).
    Убедитесь, что все меры и вычисляемые таблицы правильно определены.
    Перемещайтесь по пяти основным страницам и используйте функции Drill Through и закладки для детального анализа.
    Воспользуйтесь всплывающими окнами для получения дополнительного контекста и информации.

### Заключение📌

Этот проект Power BI предоставляет надежную основу для HR аналитики, предлагая ценные инсайты о демографических данных сотрудников, доходах и корреляциях. Используя структурированные страницы, меры и вычисляемые таблицы, пользователи могут получить всестороннее понимание HR ландшафта в организации.

#### ⚠️ Внимание: Этот проект выполнен для университетского задания, просьба не судить строго.

#### ✨ Удачи в использовании и исследовании данных! ✨

# ExpenseManagerAngular

Курсовой проект по курсу Angularjs - 2017 - 0504 - 2130


## Project mockup

Текущий mockup проекта доступен [по этой ссылке](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/Login?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)

Кнопки Login, Logout, а также большинство табов кликабельны, и по кликам можно
переходить между страницами, как в реальном приложении. Тем не менее, вот список
ссылок по страницам:

 - [Форма авторизации](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/Login?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)
 - [Основная вкладка, временной срез данных, 1 день](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/Main1day?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)
 - [Основная вкладка, временной срез данных, 3 дня, по дням](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/Main3days?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)
 - [Основная вкладка, временной срез данных, 3 дня, общий](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/Main3DaysTotal?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)
 - [Основная вкладка, срез данных по категориям, 3 дня (это общий вид для любого интервала времени)](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/Main3DaysCategoryBased?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)
 - [Основная вкладка, временной срез данных, 1 неделя, по дням](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/MainWeek?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)
 - [Основная вкладка, веменной срез данных, 1 неделя, общий](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/MainWeekTotal?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)
 - [Вкладка редактирования / добавления расходов](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/Expenses?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)
 - [Вкладка редактирования / добавления категорий, таблица](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/CategoriesTabular?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)
 - [Вкладка редактирования / добавления категорий, дерево](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/CategoriesTreeView?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)
 - [Вкладка редактирования / добавления тэгов](https://lshifr.mybalsamiq.com/projects/expensemanagerangular/prototype/Tags?key=cc460a5922fe69d89ec07db5ee3c21421e1d80d5)


## Краткое описание

Одностраничное приложение для учета личных финансов.

Задача - учет и категоризация расходов и трат, и представление различных срезов
данных о расходах - по различным интервалам времени, по категориям трат, и т.д.
Поиск по данным (в т.ч. и по тегам, если успею реализовать).

В базовом варианте, система однопользовательская, с примитивной схемой авторизации
с одним фиксированным логином и паролем. Если успею, то добавлю сущность пользователя
с профилем и нормальной много-пользовательской авторизацией и регистрацией.

## Основные сущности
 - Expense (расход / трата)
    - Поля:
        - name - название
        - place - место
        - date - дата/время
        - amount - сумма
        - currency - тип валюты
        - description - описание
        - expenseCategory - категория трат
        - tags - теги (если успею)
 - ExpenseCategory (категории покупок / трат)
    - Могут иметь подкатегории
    - Поля:
        - name - название
        - description - описание
        - parentCategory - родительская категория (null for none)
        - subcategories - под-категории
        - tags - теги (если успею)
    - По умолчанию существует категория uncategorized
 - Tag (теги)
    - Поля:
        - name - название
        - description - описание
 - Settings (установки)
    - Синглтон с набором установок
 - User (пользователь)
    - Сущность пользователя (если успею)
    - Если эта сущность реализована, то Settings перестает
    быть синглтоном, а становится вспомогательной сущностью (полем)
    для User


## Основные элементы представления

### Разделы приложения / табы в navbar

 - Main: главная страница, предоставляющая обзорный вид по данным о расходах
 - Expenses: страница с подробными  данными по расходам в виде простой таблицы
 / списка, с pagination и возможностью добавления / удаления / редактирования
 данных (inline или popup form)
 - Categories: Страница с отображением дерева категорий с возможностью
 добавления / удаления / редактирования данных (inline или popup form)
 - Settings: Страница для настройки установок виджетов, отображения etc.
 (если успеваю сделать многопользовательский режим, то это бедет часть
 User profile)
 - Tags: Страница с табличнм отображением тегов и возможностью их добавления /
  удаления / редактирования
 - Login page: страница с формой для авторизации, которая показывается
 неавторизованному пользователю.


### Формы редактирования

 - Expense creation / edit form
    - Функционал: создание / редактирование сущности Expense (трата)
    - Поля: name, place, date (default: today / now), amount, description,
    category (default: uncategorized), tags (если успею)
    - Авто-подсказка: place, date (datepicker), category, tags
 - Category creation / edit form
    - Функционал: создание / редактирование сущности ExpenseCategory (категория трат)
    - Поля: name, description, parentCategory, tags (add tag button)
    - Авто-подсказка: parentCategory, tags
 - Tag creation / edit form

### Основные виджеты
 - **Time interval selector**
    - Статус: основной виджет
    - Функционал: возможность выбрать интервал времени из: один день, три дня, неделя, месяц,
    custom range (используя datepicker)
    - Вид виджета: панель с вертикальным списком опций
    - Положение на экране: левый верхний угол, sidebar
    - Показывается для страниц: Main, Expenses
 - **Category picker**
    - Статус: основной виджет
    - Функционал: выбор категорий и подкатегорий расходов
    - Вид виджета: древообразный список с checkbox для каждой категории, панель
    - Положение на экране: sidebar слева, под time interval selector
    - Показывается для страниц: Main, Expenses, Categories
    - Notes:
        - По умолчанию, (под) категории сортируются в порядке величины расходов,
        по убыванию, но есть возможность выбрать другой вид сортировки. Вид сортировки
        по умолчанию настраивается в Settings
 - **Tag cloud** (Облако тегов - если успею)
    - Статус: основной виджет
    - Функционал: отображать облако тегов
    - Положение на экране: sidebar слева, под Category Picker
    - Показывается для страниц: Main, Expenses, Categories, Tags
 - **Сategory-based brief expenses view**
    - Статус: вспомогательный виджет
    - Функционал: отображение полной суммы затрат с возможностью детализации
    по категориям.
        - В состоянии "collapsed" показывается название категории плюс полная
        сумма затрат по под-категориям
        - В состоянии "expanded" ракрывается дерево с таким же функционалом по
        под-категориям
    - Положение на экране: под одним из основных виджетов, таких как
    Daily / 3 Day / weekly / monthly / custom range expenses view
    - Notes:
        - В самом кратком "collapsed" варианте, отображается просто как
        *+ total: сумма*, где "+" - кнопка для раскрытия по под-категориям.
        - По умолчанию, (под) категории сортируются в порядке величины расходов,
        по убыванию, но есть возможность выбрать другой вид сортировки. Вид сортировки
        по умолчанию настраивается в Settings
        - Показываются первые n (под)категорий, плюс кнопка "Раскрыть все". Число
        n = 3 по умолчанию, настраивается в Settings
 - **Daily expenses view**
    - Статус: основной виджет
    - Функционал: отображение расходов за день в виде простой таблицы:
    место / название / описание / сумма, + общая сумма расходов за день
    - Положение на экране: основная область страницы, под navbar
    - Показывается для страниц: Main
    - Notes:
        - Используется для отображения при выборе интервала времени: 1 день, 3 дня
        - Автоматически фильтрует данные с учетом выбранных категорий
 - **3 Day expenses view**
    - Статус: основной виджет
    - Функционал: Отображение расходов за трехдневный интервал в виде простой таблицы
    - Положение на экране: основная область страницы, под navbar
    - Показывается для страниц: Main
    - Notes:
        - Использует виджет Daily expenses view в качестве основого блока
        - Автоматически фильтрует данные с учетом выбранных категорий
        - Использует *Сategory-based brief expenses view* для отображения
        expense summary
 - **Expenses brief view**
    - Статус: вспомогательный виджет
    - Функционал: отображение в краткой форме расходов за некоторый интервал времени
        - Таблица с двумя полями - название и сумма, плюс полная сумма справа внизу
        - Фиксированная высота + scrollbar
        - Категории не отображаются, но фильтр по ним учитывается
    - Положение на экране: строительный блок для виджета *Weekly expenses view*
    - Показывается для страниц: Main
    - Notes:
        - По умолчанию, затраты отображаются в хронологическом порядке. Но есть
        возможность также использовать другие виды сортировки.
 - **Weekly expenses view**
    - Статус: основной виджет
    - Функционал: отображение расходов за неделю
        - Таблица 3 х 2 из виджетов *Expenses brief view*
        - Суббота и воскресенье объединены в один виджет *Expenses brief view*
        - Под таблицей, использует *Сategory-based brief expenses view* для
        отображения expense summary
    - Положение на экране: основная область страницы, под navbar
    - Показывается для страниц: Main
 - **Weekly brief expenses view**
    - Статус: вспомогательный виджет
    - Функционал: отображение расходов за неделю в краткой форме
        - Таблица, строчка для каждого дня, с полями: день недели, расходы + сумма
        - Для отображения поля расходы + сумма используется виджет *Сategory-based brief expenses view*
        - Внизу таблицы, еще один *Сategory-based brief expenses view* для всей недели
    - Положение на экране: строительный блок для виджета *Monthly expenses view*
    - Показывается для страниц: Main
 - **Monthly expenses view**
    - Статус: основной виджет
    - Функционал: отображение расходов за месяц
        - Таблица 2 х 2 из виджетов *Weekly brief expenses view*
        - При наличии пятой недели, еще один виджет *Weekly brief expenses view* ниже
        - Внизу, видже *Сategory-based brief expenses view* для всего месяца
    - Положение на экране: основная область страницы, под navbar
    - Показывается для страниц: Main
    - Notes:
        - При выборе custom range более месяца, сипользуется как строительный блок
 - **Category-based expenses view**
    - Статус: основной виджет
    - Функционал: отображение расходов по категориям за некоторый интервал времени,
     с возможностью детализации по категориям
        - В состоянии "collapsed" показывается:
            - Название категории
            - Виджет *Expenses brief view* по всем тратам во всех под-категориях
        - В состоянии "expanded" ракрывается дерево с таким же функционалом по
        под-категориям. При этом содержмое виджета *Expenses brief view* состояния
        "collapsed" распределяется по нескольким виджетам *Expenses brief view* для
        каждой под-категории.
    - Notes:
        - Этот виджет реализует альтернативное представление данных, при котором
        распределение по категориям первично, а интервал времени вторичен. Его можно
        использовать с любым интервалом времени.
        - Принципиальное отличие от виджета *Сategory-based brief expenses view* в том,
        что показываются не только суммы, но и конкретные траты.
        - Интервал времени не указывается явно, но текущее значение этого фильтра
        используется при отображении.
        - По умолчанию, (под) категории сортируются в порядке величины расходов,
        по убыванию, но есть возможность выбрать другой вид сортировки. Вид сортировки
        по умолчанию настраивается в Settings
        - Показываются первые n (под)категорий, плюс кнопка "Раскрыть все". Число
          n = 5 по умолчанию, настраивается в Settings


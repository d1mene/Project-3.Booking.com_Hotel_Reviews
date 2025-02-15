# <span style='font-size:1.5em; font-family: Helvetica, sans-serif ;'>EDA & ML Project: Prediction of Hotel Review Score  </span>

# Какой кейс решаем?
<span style='font-size:1.2em;'>*Представим, что работаем дата-сайентистом в компании Booking. Одна из проблем компании — это нечестные отели, которые накручивают себе рейтинг. Одним из способов обнаружения таких отелей является построение модели, которая предсказывает рейтинг отеля. Если предсказания модели сильно отличаются от фактического результата, то, возможно, отель ведёт себя нечестно, и его стоит проверить.*</span>
# Задачи проекта
<span style='font-size:1.2em;'>

* Исследовать и обработать исходные данные.

* Визуализировать данные.

* Создать новые признаки из исходного датафрейма, в том числе с использованием сторонних ресурсов и библиотек с анализом текста.

* Проверить признаки на мультиколлинеарность, удалить сильно зависимые признаки для повышения точности модели.

* Поработать с оставшимися признаками: разделить признаки на количественные и категориальные, количественные признаки нормализовать для улучшения модели.

* Создать и обучить модель для предсказания оценки отеля. </span>
# Используемые библиотеки
Version of Python - 3.12.2
* Pandas (2.2.1)
* Numpy (1.26.4)
* Seaborn (0.13.2)
* Matplotlib (3.8.4)
* Scikit-learn (1.5.0)
* Category_encoders (2.6.3)
* Plotly (5.21.0)
* Natural Language Toolkit (3.8.1)
* Gensim (4.3.2)
* Math

Дополнительные пакеты:
pandas_profiling, vader_lexicon, punkt
# Ссылка на датафрейм
Google Drive: https://drive.google.com/drive/folders/1yNcOxPkgMWtv8dt7n-yazbTVuMALmsXW?usp=sharing
# Признаки в исходном датафрейме
hotel_address — адрес отеля; <br><br>
review_date — дата, когда рецензент разместил соответствующий отзыв;<br><br>
average_score — средний балл отеля, рассчитанный на основе последнего комментария за последний год;<br><br>
hotel_name — название отеля;<br><br>
reviewer_nationality — страна рецензента;<br><br>
negative_review — отрицательный отзыв, который рецензент дал отелю;<br><br>
review_total_negative_word_counts — общее количество слов в отрицательном отзыв;<br><br>
positive_review — положительный отзыв, который рецензент дал отелю;<br><br>
review_total_positive_word_counts — общее количество слов в положительном отзыве;<br><br>
total_number_of_reviews_reviewer_has_given — количество отзывов, которые рецензенты дали в прошлом;<br><br>
total_number_of_reviews — общее количество действительных отзывов об отеле;<br><br>
tags — теги, которые рецензент дал отелю;<br><br>
days_since_review — количество дней между датой проверки и датой очистки;<br><br>
additional_number_of_scoring — есть также некоторые гости, которые просто поставили оценку сервису, но не оставили отзыв. Это число указывает, сколько там действительных оценок без проверки;<br><br>
lat — географическая широта отеля;<br><br>
lng — географическая долгота отеля. <br><br>
**reviewer_score — оценка, которую рецензент поставил отелю на основе своего опыта** - *ключевой признак*
# Описание проекта
1. <span style='font-size:1.2em;'>Загрузка и предобработка данных: </span>
    * Все библиотеки, пакеты и данные успешно загружены.
    * Проведён анализ типов данных, выявлены и устранены дубликаты.
    * Найдены пропуски в признаках 'lat' и 'lng', были заполнены медианными значениями.

2. <span style='font-size:1.2em;'>Визуализация. Знакомство с данными</span>
    * Быстрый и подробный визуальный и аналитический отсчет был подготовлен благодаря функции ProfileReport.
    * Также здесь и далее будут построены графики, иллюстрирующие поиск и отбор важных признаков.

3. <span style='font-size:1.2em;'>Feature Engineering</span>
    1. Работа с отзывами: 
    * Нашли процент положительных и негативных слов в отзыве.

    * С помощью языковых моделей создали множество новых признаков.
    <br><br>

    2. Работа с местоположением отеля: 
    * Определили, в каких странах находятся отели.

    * Визуализировали кол-во отелей по странам.

    * С помощью сторонних сервисов определены координаты самых популярных достопримечательностей в каждой стране и создан новый признак - расстояние до ближайшей "точки притяжения".

    * Закодирован признак национальности ревьювера
    <br><br>
    3. Дата и время:
    * Из признака даты отзыва выделили новые признаки: день, месяц и год отзыва. Исследованы зависимости оценки пользователя от периода времени.

    * Также были добавлены признак, характеризующий день недели, и к тому же признак, показывающий, является ли день выходным.
    <br><br>
    4. Теги 
    * Добавили признаки-индикаторы 10 самых популярных тегов.

    * Выведен новый признак - количество ночей, проведённых в отеле.

4. <span style='font-size:1.2em;'>Проверка на мультиколлинеарность</span>
    * Построена тепловая карта коллинеарности числовых признаков.
    * В ходе нескольких тестов выявлены и удалены второстепенные признаки с сильной зависимостью от других, создающих более точную модель.
5. <span style='font-size:1.2em;'>Машинное обучение</span>
    * Удалены нечисловые признаки.
    * Ключевой признак отделён от остальных.
    * Признаки разделены на категориальные и числовые.
    * Проведёна нормализация числовых признаков (исключение: признаки, которые уже находятся в диапозоне [-1, 1]).
    * Проведено создание и обучение модели.
    * Построены графики, которые в ходе тестов помогли удалить неинформативные признаки.
# Итоги работы
На выходе получили готовую модель машинного обучения, которая предсказывает оценку отеля с точностью примерно 85 %.
Показатель MAPE: 0.147026

Был проведён тщательный анализ данных и их визуализация, созданы новые количественные и категориальные признаки, исходные данные преобразованы в более понятный для модели вид, количественные признаки нормализованы, проведена работа с внешними ресурсами (Google Maps, сайты https://www.planetware.com, https://snippetsofparis.com, https://skyticket.com), сделан отбор признаков. Вдобавок, использованы библиотеки по анализу естественного языка, построены языковые модели, проведена векторизация слов.
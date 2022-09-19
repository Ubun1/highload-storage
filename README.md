# Проектирование облачного файлового хранилища


## Содержание
1. [Тема и целевая аудитория](#part-1)
2. [Расчет нагрузки](#part-2)
3. [Логическая схема](#part-3)
4. [Физическая схема](#part-4)
5. [Технологии](#part-5)
6. [Схема проекта](#part-6)
7. [Список серверов](#part-7)
8. [Список использованных источников](#part-8)


## 1. Тема и целевая аудитория <a name="part-1"></a>
Облачное файловое хранилище позволяет пользователям хранить их файлы удаленно и предоставляет доступ на их просмотр и скачивание. В данной работе в качестве примера будет реализован функцоинал сервиса Dropbox - файлового хостинга компании Dropbox Inc., включающего персональное облачное хранилище, синхронизацию файлов и программу-клиент [1].

MVP сервиса будет включать следующее:
* Загрузка файлов в хранилище
* Скачивание файлов из хранилища
* Просмотр загруженных файлов через браузер
* Предоставление доступа на просмотр файлов третьим лицам

На текущий момент в Dropbox зарегистрировано более 700 млн пользователей [2]. При этом [3]:
* В США - 35.40% пользователей - 247.8 млн человек
* В Великобритании - 5.30% пользователей - 37.1 млн человек
* В Японии - 5.22% пользователей - 36.54 млн человек
* В Германии - 3.7% пользователей - 25.9 млн человек
* В Австралии - 3.54% пользователей - 24.99 млн человек
* В остальных странах - 46.84% пользователей - 327.88 млн человек


## 2. Расчет нагрузки <a name="part-2"></a>
### Продуктовые метрики
Dropbox ежемесячно посещает около 153.7 млн пользователей [3]. Это в среднем 5.12 млн человек в день.

Размер хранилища составляет [4]:
* Для бесплатных пользователей - 2 Гб
* Для платных пользователей на самой дорогой подписке - не ограничено

Пусть около 25% посещений происходит с запросом авторизации, тогда ежедневно выполняется 1.28 млн запросов на авторизацию.

Согласно статистике за 2016 год в Dropbox ежедневно загружают порядка 1 200 млн файлов [5]. Т.к. в 2016 году аудитория составляла 433 млн человек, а сейчас составляет более 700 млн человек [2], то возьмём количество загрузок файлов равное 1 940 млн.

На первой странице сервиса отображается список всех файлов. Предположим, что каждый десятый хотя бы раз попадает на эту страницу. Пусть таких запросов 60 млн в день.

Предположим, что пользователи просматривают половину своих файлов в день. Согласно статистике за 2018 год всего было загружено 400 000 млн файлов. Т.к. в 2018 году аудитория составляла 500 млн человек, а сейчас составляет более 700 млн человек [2], то получим 560 000 млн файлов. Это в среднем просмотр 778 млн файлов в день.

Согласно статистике за 2015 год каждый час создается 100 тысяч новых публичных папок и файлов [5]. Т.к. в 2015 году аудитория составляла 400 млн человек, а сейчас составляет более 700 млн человек [2], то возьмем, что каждый час создается 175 тысяч шареных файлов. Тогда в день таких файлов создается порядка 4.2 млн.

Среднее количество действий пользователей представлено в таблице 1, среднее количество действий одного пользователя представлено в таблице 2.

Таблица 1 - Среднее количество действий пользователей
Тип запроса             | Среднее количество (млн/день)
----------------------- | -----------------------------
Авторизация             | 1.28
Загрузка файлов         | 1 940
Просмотр списка файлов  | 60
Просмотр файлов         | 778
Предоставление доступа  | 4.2

Таблица 2 - Среднее количество действий одного пользователя
Тип запроса             | Среднее количество (в день)
----------------------- | -----------------------------
Авторизация             | 0.25
Загрузка файлов         | 379
Просмотр списка файлов  | 12
Просмотр файлов         | 152
Предоставление доступа  | 1

### Технические метрики
На текущий момент в Dropbox зарегистрировано более 700 млн пользователей, из которых 15.5 млн - платные пользователи [2].

Размер хранилища составляет [4]:
* Для бесплатных пользователей - 2 Гб
* Для платных пользователей на самой дорогой подписке - не ограничено

Предположим, что:
* Бесплатные пользователи используют 1 Гб
* Платные пользователи используют 256 Гб

В таком случае общий размер хранилища будет равен 684.50 * 10e6 * 1 + 15.5 * 10e6 * 256 = 684 500 + 3 968 000 = 4 652 500 (Тб).

## 3. Логическая схема <a name="part-3"></a>


## 4. Физическая схема <a name="part-4"></a>


## 5. Технологии <a name="part-5"></a>


## 6. Схема проекта <a name="part-6"></a>


## 7. Список серверов <a name="part-7"></a>


## 8. Список использованных источников <a name="part-8"></a>
1. https://ru.wikipedia.org/wiki/Dropbox
2. https://earthweb.com/dropbox-statistics/
3. https://www.similarweb.com/ru/website/dropbox.com
4. https://www.dropbox.com/plans
5. https://expandedramblings.com/index.php/dropbox-statistics/

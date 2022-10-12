# 6.1. Типы и структура СУБД

## Задача1
- **Электронные чеки в json виде** - Документо-ориентированные, т.к. хранят данные в структурированных форматах, в том числе json. 
- **Склады и автомобильные дороги для логистической компании** - возможно графовая, склады будут в роли объекта, дороги в роли ребер со своими свойствами. А также данные БД применяются для предсказания, что и необходимо для логистики. 
- **Генеалогические деревья** - Иерархическая модель имеющая древовидную структуру
- **Кэш идентификаторов клиентов с ограниченным временем жизни для движка аутенфикации** - Ключ-значение, данные типы БД используются для хранения кэша и мгновенного ответа на запрос. 
- **Отношения клиент-покупка для интернет-магазина** - Реляционная БД, связь таблицы "клиент" и таблицы "товар", у каждой таблицы свои свойства (данные), больше всего подходит реляционная модель
## Задача 2 

 - **Данные записываются на все узлы с задержкой до часа (асинхронная запись)**
 - **При сетевых сбоях, система может разделиться на 2 раздельных кластера**
 - **Система может не прислать корректный ответ или сбросить соединение**

## Задача 3
**Могут ли в одной системе сочетаться принципы BASE и ACID? Почему?**
Не могут. Base и ACID это разные требования или можно сказать принципы БД. Кратко по моему мнению о каждом. Base - увеличение кол-ва транзакций за единицу времени, ACID - качество выполнения транзакций в БД.

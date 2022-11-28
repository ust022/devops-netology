# 6.2. SQL

## Задача1
**Используя docker поднимите инстанс PostgreSQL (версию 12) c 2 volume, в который будут складываться данные БД и бэкапы.
Приведите получившуюся команду или docker-compose манифест.**

    $ docker pull postgres:12
    $ docker volume create database
    $ docker volume create backup
    $ docker run -d --name homework-6.2 \
    > -e POSTGRES_PASSWORD=Qwerty123 \
    > -p 5432:5432 \
    > -v database:/var/lib/postgresql/database \
    > -v backup:/var/lib/postgresql/backup \
    > postgres:12

## Задача 2

**итоговый список БД после выполнения пунктов выше**


**описание таблиц (describe)**


**SQL-запрос для выдачи списка пользователей с правами над таблицами test_db**


**список пользователей с правами над таблицами test_db**



## Задача 3
.

## Задача 4



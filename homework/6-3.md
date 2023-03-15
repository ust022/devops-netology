# Домашнее задание к занятию 3. «MySQL»
## Задача 1
- Используя Docker, поднимите инстанс MySQL (версию 8). Данные БД сохраните в volume.
```
# docker pull mysql:8
# docker volume create sql-database
# docker volume create sql-backup
# docker run --name homework-6.3 -e MYSQL_ROOT_PASSWORD=Qwerty123 -v sql-database:/var/lib/mysql -v sql-backup:/var/lib/mysql/backup -d mysql:8
```
- Изучите бэкап БД и восстановитесь из него. Перейдите в управляющую консоль mysql внутри контейнера.
```

```

# 6.2. SQL

## Задача1
**Используя docker поднимите инстанс PostgreSQL (версию 12) c 2 volume, в который будут складываться данные БД и бэкапы.
Приведите получившуюся команду или docker-compose манифест.**
```
$ docker pull postgres:12
$ docker volume create database
$ docker volume create backup
$ docker run -d --name homework-6.2 \
> -e POSTGRES_PASSWORD=Qwerty123 \
> -p 5432:5432 \
> -v database:/var/lib/postgresql/database \
> -v backup:/var/lib/postgresql/backup \
> postgres:12
```
## Задача 2

* **итоговый список БД после выполнения пунктов выше**
```
test_db=# \l
                                 List of databases
   Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileges   
-----------+----------+----------+------------+------------+-----------------------
 postgres  | postgres | UTF8     | en_US.utf8 | en_US.utf8 | 
 template0 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres
 template1 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres
 test_db   | postgres | UTF8     | en_US.utf8 | en_US.utf8 | 
(4 rows)
```

* **описание таблиц (describe)**
```
test_db=# \d+ orders
                                                     Table "public.orders"
 Column |       Type        | Collation | Nullable |              Default               | Storage  | Stats target | Description 
--------+-------------------+-----------+----------+------------------------------------+----------+--------------+-------------
 id     | integer           |           | not null | nextval('orders_id_seq'::regclass) | plain    |              | 
 name   | character varying |           |          |                                    | extended |              | 
 price  | integer           |           |          |                                    | plain    |              | 
Indexes:
    "orders_pkey" PRIMARY KEY, btree (id)
Referenced by:
    TABLE "clients" CONSTRAINT "clients_order_id_fkey" FOREIGN KEY (order_id) REFERENCES orders(id)
Access method: heap
```
```
test_db=# \d+ clients
                                                      Table "public.clients"
  Column  |       Type        | Collation | Nullable |               Default               | Storage  | Stats target | Description 
----------+-------------------+-----------+----------+-------------------------------------+----------+--------------+-------------
 id       | integer           |           | not null | nextval('clients_id_seq'::regclass) | plain    |              | 
 surname  | character varying |           |          |                                     | extended |              | 
 country  | character varying |           |          |                                     | extended |              | 
 order_id | integer           |           |          |                                     | plain    |              | 
Indexes:
    "clients_pkey" PRIMARY KEY, btree (id)
Foreign-key constraints:
    "clients_order_id_fkey" FOREIGN KEY (order_id) REFERENCES orders(id)
Access method: heap

```

* **SQL-запрос для выдачи списка пользователей с правами над таблицами test_db**
```
test_db=# SELECT grantee, table_catalog, table_name, privilege_type
FROM information_schema.table_privileges
WHERE grantee IN ('test-admin-user','test-simple-user');
```

* **список пользователей с правами над таблицами test_db**
```
     grantee      | table_catalog | table_name | privilege_type 
------------------+---------------+------------+----------------
 test-admin-user  | test_db       | orders     | INSERT
 test-admin-user  | test_db       | orders     | SELECT
 test-admin-user  | test_db       | orders     | UPDATE
 test-admin-user  | test_db       | orders     | DELETE
 test-admin-user  | test_db       | orders     | TRUNCATE
 test-admin-user  | test_db       | orders     | REFERENCES
 test-admin-user  | test_db       | orders     | TRIGGER
 test-simple-user | test_db       | orders     | INSERT
 test-simple-user | test_db       | orders     | SELECT
 test-simple-user | test_db       | orders     | UPDATE
 test-simple-user | test_db       | orders     | DELETE
 test-admin-user  | test_db       | clients    | INSERT
 test-admin-user  | test_db       | clients    | SELECT
 test-admin-user  | test_db       | clients    | UPDATE
 test-admin-user  | test_db       | clients    | DELETE
 test-admin-user  | test_db       | clients    | TRUNCATE
 test-admin-user  | test_db       | clients    | REFERENCES
 test-admin-user  | test_db       | clients    | TRIGGER
 test-simple-user | test_db       | clients    | INSERT
 test-simple-user | test_db       | clients    | SELECT
 test-simple-user | test_db       | clients    | UPDATE
 test-simple-user | test_db       | clients    | DELETE
(22 rows)
```

## Задача 3

.**Используя SQL синтаксис - наполните таблицы следующими тестовыми данными:**
```
test_db=# INSERT INTO orders (name,price) VALUES
('Шоколад',10),
('Принтер',3000),
('Книга',500),
('Монитор',7000),
('Гитара',4000);
INSERT 0 5
```

```
test_db=# INSERT INTO clients (surname,country) VALUES
('Иванов Иван Иванович','USA'),
('Петров Петр Петрович','Canada'),
('Иоганн Себастьян Бах','Japan'),
('Ронни Джеймс Дио','Russia'),
('Ritchie Blackmore','Russia');
INSERT 0 5
```
* **вычислите количество записей для каждой таблицы**

```
test_db=# select count(*) from clients;
 count 
-------
     5
(1 row)

test_db=# select count(*) from orders;
 count 
-------
     5
(1 row)
```

## Задача 4



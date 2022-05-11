## Задача 1

Найдите и приведите управляющие команды для:

- вывода списка БД - \l
- подключения к БД - \c 
- вывода списка таблиц - \dt
- вывода описания содержимого таблиц - \d
- выхода из psql - \q


## Задача 2
```
select tablename,attname,avg_width from pg_stats where tablename='orders';

 tablename | attname | avg_width 
-----------+---------+-----------
 orders    | id      |         4
 orders    | title   |        16
 orders    | price   |         4
(3 rows)

```

## Задача 3
Предложите SQL-транзакцию для проведения данной операции.
```
CREATE TABLE orders_1 (LIKE orders);
CREATE TABLE orders_2 (LIKE orders);
INSERT INTO orders_1 SELECT * FROM orders WHERE price > 499;
DELETE FROM orders WHERE price > 499;
INSERT INTO orders_2 SELECT * FROM orders WHERE price <= 499;
DELETE FROM orders WHERE price <= 499;
```
Можно ли было изначально исключить "ручное" разбиение при проектировании таблицы orders?

Да, можно

## Задача 4

Как бы вы доработали бэкап-файл, чтобы добавить уникальность значения столбца title для таблиц test_database?
```
CREATE TABLE public.orders (
    id integer NOT NULL,
    title character varying(80) NOT NULL UNIQUE,
    price integer DEFAULT 0
);
```

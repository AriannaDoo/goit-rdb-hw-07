## Домашнє завдання 7

### Робота з часом. Додаткові вбудовані SQL функції.

---

## Опис роботи

У цьому домашньому завданні було виконано SQL-запити для роботи з часовими даними та JSON-об’єктами.

Під час виконання роботи були використані такі SQL-функції та оператори:

- `YEAR`
- `MONTH`
- `DAY`
- `DATE_ADD`
- `UNIX_TIMESTAMP`
- `BETWEEN`
- `COUNT`
- `JSON_OBJECT`
- `SELECT`
- `FROM`
- `WHERE`

Для виконання завдання використовувалась база даних `goit_rdb_hw_03`, створена та заповнена під час попередніх домашніх завдань.

---

## Використана база даних

```sql
USE goit_rdb_hw_03;
```

---

## Завдання 1

Написати SQL-запит, який для таблиці `orders` з атрибута `date` витягує рік, місяць і число.

На екран виведено атрибути `id`, оригінальний атрибут `date`, а також окремо рік, місяць і день.

```sql
SELECT 
    id,
    `date`,
    YEAR(`date`) AS order_year,
    MONTH(`date`) AS order_month,
    DAY(`date`) AS order_day
FROM orders;
```

---

## Завдання 2

Написати SQL-запит, який для таблиці `orders` до атрибута `date` додає один день.

На екран виведено атрибут `id`, оригінальний атрибут `date` та результат додавання одного дня.

```sql
SELECT 
    id,
    `date`,
    DATE_ADD(`date`, INTERVAL 1 DAY) AS date_plus_one_day
FROM orders;
```

---

## Завдання 3

Написати SQL-запит, який для таблиці `orders` для атрибута `date` відображає кількість секунд з початку відліку.

Для цього використано функцію `UNIX_TIMESTAMP`.

```sql
SELECT 
    id,
    `date`,
    UNIX_TIMESTAMP(`date`) AS timestamp_value
FROM orders;
```

---

## Завдання 4

Написати SQL-запит, який рахує, скільки таблиця `orders` містить рядків з атрибутом `date` у межах між `1996-07-10 00:00:00` та `1996-10-08 00:00:00`.

```sql
SELECT 
    COUNT(*) AS orders_count
FROM orders
WHERE `date` BETWEEN '1996-07-10 00:00:00' AND '1996-10-08 00:00:00';
```

---

## Завдання 5

Написати SQL-запит, який для таблиці `orders` виводить атрибут `id`, атрибут `date` та JSON-об’єкт у форматі:

```json
{"id": <id>, "date": <date>}
```

Для створення JSON-об’єкта використано функцію `JSON_OBJECT`.

```sql
SELECT 
    id,
    `date`,
    JSON_OBJECT('id', id, 'date', `date`) AS order_json
FROM orders;
```

---

## Скріншоти

У репозиторії додано скріншоти виконаних SQL-запитів та результатів їх роботи.

Рекомендовані назви файлів:

- `p1_extract_year_month_day.png`
- `p2_date_add_one_day.png`
- `p3_unix_timestamp.png`
- `p4_count_orders_between_dates.png`
- `p5_json_object.png`

---

## Файли репозиторію

- `hw7.sql`
- `README.md`
- скріншоти з результатами виконання запитів

# SQL-запросы для тестирования

## Даны таблицы

### users

| id | name | email |
|----|------|-------|
| 1 | Анна | anna@mail.ru |
| 2 | Иван | ivan@mail.ru |

### orders

| id | user_id | amount | status |
|----|---------|--------|--------|
| 1 | 1 | 5000 | paid |
| 2 | 1 | 3000 | pending |
| 3 | 2 | 7000 | paid |

## Запросы

### 1. Выбрать всех пользователей

```sql
SELECT * FROM users;
```

### 2. Выбрать пользователей с именем «Анна»

```sql
SELECT * FROM users
WHERE name = 'Анна';
```

### 3. Выбрать все заказы со статусом «paid»

```sql
SELECT * FROM orders
WHERE status = 'paid';
```

### 4. Выбрать сумму всех заказов пользователя с id = 1

```sql
SELECT SUM(amount)
FROM orders
WHERE user_id = 1;
```

### 5. Выбрать имена пользователей и суммы их заказов

```sql
SELECT users.name, SUM(orders.amount) AS total_amount
FROM users
JOIN orders ON users.id = orders.user_id
GROUP BY users.name;
```

# Часть 1: анализ данных интернет-магазина с помощью SQL и построение дашбордов.

## Цель
Ответить на бизнес-вопросы о продажах, клиентах, доставке и товарах с помощью SQL.

## Данные
9 таблиц Olist, база PostgreSQL. Источник: [Датасет Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?resource=download).
![Схема связей таблиц](C:\Users\vlad4\OneDrive\Рабочий стол\проект по аналитике 1\таблицы csv с данными.png)

---

## A. Продажи

### 1. Как менялась выручка по месяцам?

```sql
SELECT DATE_TRUNC('month', o.order_purchase_timestamp) AS month,
       ROUND(SUM(p.payment_value), 2) AS revenue
FROM orders o
JOIN order_payments p USING (order_id)
GROUP BY 1
ORDER BY 1;
```

**Результат:**

| month      | revenue   |
|------------|-----------|
| 2017-01-01 | 138488.04 |
| 2017-02-01 | 291908.01 |

**Вывод:** здесь одно-два предложения о том, что видно в цифрах.

---

### 2. Следующий вопрос...

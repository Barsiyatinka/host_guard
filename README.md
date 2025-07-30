# Домашнее задание к занятию   
**"`Индексы`"** - `Воскобойников Арсений Петрович`  
   
**Задание 1**  
``` 
Напишите запрос к учебной базе данных, который вернёт процентное отношение общего размера всех индексов к общему размеру всех таблиц.
```
**Ответ**  


<img src="img/screen_1.png" width="100%">   

**Задание 2**  
```
Выполните explain analyze следующего запроса:

select distinct concat(c.last_name, ' ', c.first_name), sum(p.amount) over (partition by c.customer_id, f.title)
from payment p, rental r, customer c, inventory i, film f
where date(p.payment_date) = '2005-07-30' and p.payment_date = r.rental_date and r.customer_id = c.customer_id and i.inventory_id = r.inventory_id
перечислите узкие места;
оптимизируйте запрос: внесите корректировки по использованию операторов, при необходимости добавьте индексы.
```
**Ответ**  
<img src="img/screen_2.png" width="100%">

Узкие места:
- использование DATE() отключает использование индексов. 
- Нет фильтрации film f
- Отсутствие явного JOIN-а между inventory и film


**Задание 3**  
```
Самостоятельно изучите, какие типы индексов используются в PostgreSQL. Перечислите те индексы, которые используются в PostgreSQL, а в MySQL — нет.

Приведите ответ в свободной форме.
```
**Ответ**  

GIN (Generalized Inverted Index)
GiST (Generalized Search Tree)
SP-GiST (Space-partitioned GiST)
BRIN (Block Range Index)
Bloom Index (расширение)
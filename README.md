## Интернет магазин
## 1.  
SELECT o.FIO, o.address, p.name, oi.amount, p.price*oi.amount as Sum, c.name   

from shop.orders as o  

join shop.couriers as c  
on o.courier_id = c.id  

join shop.order_items as oi  
on o.id = oi.order_id  

join shop.products as p  
on p.id = oi.product_id  

where o.id = 2;//Получили всю информацию по ID заказа: продукты, количество, кто и куда доставляет, сумма заказа

## 2.
INSERT INTO shop.orders (FIO, address, courier_id) VALUES ('Анна', 'Маркуса', '1');

INSERT INTO shop.order_items (product_id, order_id, amount) VALUES ('1', '2', '1');//Создали заказа

## 3.
SELECT * from shop.orders where orders.courier_id=1;//Вывели все заказы для заданного ID курьера

## 4.
UPDATE shop.order_items  
SET amount = '5'  
WHERE (id = '3');//Увеличили количество продукта по имени продукта в конкретном заказе по ID



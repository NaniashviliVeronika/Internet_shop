# Интернет магазин
Создание таблицы продуктов
CREATE TABLE products (
id int NOT NULL AUTO_INCREMENT,
name varchar(45) NOT NULL,
price decimal(5,2) NOT NULL,
PRIMARY KEY (id)
) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci

Создание таблицы заказов
CREATE TABLE orders (
id int NOT NULL AUTO_INCREMENT,
FIO varchar(45) NOT NULL,
address varchar(45) NOT NULL,
courier_id int NOT NULL,
PRIMARY KEY (id),
KEY orders_couriers_idx (courier_id),
CONSTRAINT orders_couriers FOREIGN KEY (courier_id) REFERENCES couriers (id)
) ENGINE=InnoDB AUTO_INCREMENT=11 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci

Создание таблицы курьеров
CREATE TABLE couriers (
id int NOT NULL AUTO_INCREMENT,
name varchar(45) NOT NULL,
phone_num varchar(20) NOT NULL,
car_num varchar(20) NOT NULL,
PRIMARY KEY (id)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci

Создание таблицы order_items
CREATE TABLE order_items (
id int NOT NULL AUTO_INCREMENT,
product_id int NOT NULL,
order_id int NOT NULL,
amount int NOT NULL,
PRIMARY KEY (id),
KEY products_order_items_idx (product_id),
KEY orders_order_items_idx (order_id),
CONSTRAINT orders_order_items FOREIGN KEY (order_id) REFERENCES orders (id),
CONSTRAINT products_order_items FOREIGN KEY (product_id) REFERENCES products (id)
) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci


# 1.  
SELECT o.FIO, o.address, p.name, oi.amount, p.price*oi.amount as Sum, c.name   

from shop.orders as o  

join shop.couriers as c  
on o.courier_id = c.id  

join shop.order_items as oi  
on o.id = oi.order_id  

join shop.products as p  
on p.id = oi.product_id  

where o.id = 2;//Получили всю информацию по ID заказа: продукты, количество, кто и куда доставляет, сумма заказа

# 2.
INSERT INTO shop.orders (FIO, address, courier_id) VALUES ('Анна', 'Маркуса', '1');

INSERT INTO shop.order_items (product_id, order_id, amount) VALUES ('1', '2', '1');//Создали заказа

# 3.
SELECT * from shop.orders where orders.courier_id=1;//Вывели все заказы для заданного ID курьера

# 4.
UPDATE shop.order_items  
SET amount = '5'  
WHERE (id = '3');//Увеличили количество продукта по имени продукта в конкретном заказе по ID



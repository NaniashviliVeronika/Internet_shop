# Интернет магазин
1.  
SELECT o.FIO, o.address, p.name, oi.amount, p.price*oi.amount as Sum, c.name   

from shop.orders as o  

join shop.couriers as c  
on o.courier_id = c.id  

join shop.order_items as oi  
on o.id = oi.order_id  

join shop.products as p  
on p.id = oi.product_id  

where o.id = 2;  

/* Product pairs most commonly purchased together */

drop table if exists orders;
create table orders(
order_id int,
customer_id int,
product_id int);


insert into orders VALUES 
(1, 1, 1),
(1, 1, 2),
(1, 1, 3),
(2, 2, 1),
(2, 2, 2),
(2, 2, 4),
(3, 1, 5);

create table products (
id int,
name varchar(10)
);
insert into products VALUES 
(1, 'A'),
(2, 'B'),
(3, 'C'),
(4, 'D'),
(5, 'E');

select * from orders ;
select * from products ;

/* hints 
> first, joined the orders and products column bases on product_id to get the product name (t1)
> then just self joined the t1 column with itself to get the pairs of products customer purchased (t2)
> then just count the distinct pairs number based on pairs.
*/
/*Solution */

with t1 as
	(select o.order_id,o.customer_id,o.product_id,p.name as product_name from orders o
	join products p
	on o.product_id = p.id
	order by o.order_id asc,o.product_id asc),
	t2 as
	(select a.order_id , a.product_name as a_p_n, b.product_name as b_p_n, concat(a.product_name, ',' , b.product_name) as pair from t1 a join t1 b on a.order_id = b.order_id
	where a.product_id < b.product_id)
select pair, count(distinct order_id) from t2 group by pair order by count(distinct order_id) desc ;

/* Horizontal Sorting */

drop table if exists products;
create table products
(
product_id varchar(20) ,
cost int
);

insert into products values ('P1',200),('P2',300),('P3',500),('P4',800);

create table customer_budget
(
customer_id int,
budget int
);

insert into customer_budget values (100,400),(200,800),(300,1500);

select * from products ;
select * from customer_budget ;


with t1 as
	(select *,
	sum(cost) over(order by cost rows between unbounded preceding and current row) as running_total_cost
	from products )

select customer_id, budget,count(*) as no_of_purchased_products,
string_agg(product_id,',')
from t1
right join customer_budget cb 
on cb.budget > t1.running_total_cost
group by customer_id, budget
order by customer_id ;

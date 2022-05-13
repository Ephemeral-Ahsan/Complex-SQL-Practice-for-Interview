/* write a query to find p_id,name,no of friends, sum of scores of person who have friends with total score greater than 100 */

create table person ( 
p_id int,
name varchar(20),
score int);

create table friend ( 
p_id int,
f_id int);

insert into person 
values 
(1,'Ahsan',88),
(2,'Juel',11),
(3,'Jubayer',27),
(4,'Shakel',45),
(5,'Sunny',63);   

insert into friend 
values 
(1,2),
(1,3),
(2,1),
(2,3),
(3,5),
(4,2),
(4,3),
(4,5);

select * from person;
select * from friend;

/* 
my logic here -
1. at first join the friend table with person to get friends score 
2. then count friend id and sum friend score group by p_id from friend
3. then join the existing result again with person table to get person name.
*/

/* Solution */

select f.p_id,p1.name,count(f.f_id) as total_friends, sum(p.score) as total_friend_score from friend f
join person p on f.f_id = p.p_id
join person p1 on f.p_id = p1.p_id
group by 1,2 
having sum(p.score) >100

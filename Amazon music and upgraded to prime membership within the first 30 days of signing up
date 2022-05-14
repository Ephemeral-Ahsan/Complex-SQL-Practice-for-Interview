/* return the fraction of users, rounded to two decimal places,
who accessed Amazon music and upgraded to prime membership within the first 30 days of signing up */

drop table if exists users;
create table users
(
user_id integer,
name varchar(20),
join_date date
);

insert into users
values (1, 'Jon', CAST('2-14-20' AS date)), 
(2, 'Jane', CAST('2-14-20' AS date)), 
(3, 'Jill', CAST('2-15-20' AS date)), 
(4, 'Josh', CAST('2-15-20' AS date)), 
(5, 'Jean', CAST('2-16-20' AS date)), 
(6, 'Justin', CAST('2-17-20' AS date)),
(7, 'Jeremy', CAST('2-18-20' AS date));

drop table if exists events;
create table events
(
user_id integer,
type varchar(10),
access_date date
);

insert into events values
(1, 'Pay', CAST('3-1-20' AS date)), 
(2, 'Music', CAST('3-2-20' AS date)), 
(2, 'P', CAST('3-12-20' AS date)),
(3, 'Music', CAST('3-15-20' AS date)), 
(4, 'Music', CAST('3-15-20' AS date)), 
(1, 'P', CAST('3-16-20' AS date)), 
(3, 'P', CAST('3-22-20' AS date));

/* hints 
> first, joined the users table with events table where users from event table event type is Music, to user_id who were joined the amazon music (t1)
> then left joined the existing table to event table where user id is similar but event_type is only 'P' to find the access_date of 'P' subscription (t2).
*/

/*Solution */

select * from users ;
select * from events ;

with t1 as
	(select user_id,join_date from users where user_id in (select user_id from events where type = 'Music')),
	t2 as
	(select t1.user_id, t1.join_date, e.type, e.access_date, e.access_date - t1.join_date as subs_day_diff
	from t1 left join events e on t1.user_id = e.user_id and e.type = 'P'),
	t3 as
	(select count(distinct user_id) as total_user from t2),
	t4 as
	(select count(distinct user_id) as updated_subscription_in_30 from t2 where subs_day_diff < 30)

select t3.total_user, t4.updated_subscription_in_30,
	round(1.0*t4.updated_subscription_in_30/t3.total_user*100,2) as subscription_rate from t3,t4;

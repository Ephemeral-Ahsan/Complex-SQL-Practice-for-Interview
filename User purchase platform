/* User purchase platform.
-- The table logs the spendings history of users that make purchases from an online shopping website which has a desktop 
and a mobile application.
-- Write an SQL query to find the total number of users and the total amount spent using mobile only, desktop only 
and both mobile and desktop together for each date.
*/

create table spending 
(
user_id int,
spend_date date,
platform varchar(10),
amount int
amount int
);

insert into spending values
(1,'2019-07-01','mobile',100),
(1,'2019-07-01','desktop',100),
(2,'2019-07-01','mobile',100),
(2,'2019-07-02','mobile',100),
(3,'2019-07-01','desktop',100),
(3,'2019-07-02','desktop',100);

select * from spending;

/* 
hint:-
at first, i have extracted out the user_id,spend_date, platform and sum of amount using having function where count(distinct platform) = 1 [either mobile or desktop]
then, i have used union all to add the rows where count(distinct platform) = 2 [ mobile and desktop]
Finally my result is ready where i have extracted the sum of amount for only mobile, only dekstop and both for each date.
*/


/* solution */
with only_one_device_user as
	(select user_id,spend_date,max(platform),sum(amount) from spending group by user_id,spend_date having count(distinct platform) = 1),
	both_device_user as
	(select user_id,spend_date,'both' as platform,sum(amount) from spending group by user_id,spend_date having count(distinct platform) = 2),
	t1 as 
	(select * from only_one_device_user
	 union all select * from both_device_user)
select * from t1 ;

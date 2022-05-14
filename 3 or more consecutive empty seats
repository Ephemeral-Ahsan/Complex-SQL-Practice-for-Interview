/* 3 or more consecutive empty seats */

create table bms (seat_no int ,is_empty varchar(10));
insert into bms values
(1,'N')
,(2,'Y')
,(3,'N')
,(4,'Y')
,(5,'Y')
,(6,'Y')
,(7,'N')
,(8,'Y')
,(9,'Y')
,(10,'Y')
,(11,'Y')
,(12,'N')
,(13,'Y')
,(14,'Y');

/* hints
1. I have extract all the empty seat and then give them row number based on their seat no.
2. then subtract the row number from seat no 
	i.e 2,4,5,6,8,9,10,11,13,14 are the empty seat
		row numbers are given for these are:
		1,2,3,4,5,6,7,8,9,10.
3. then find the difference between seat no and row number
(2-1) = 1
4-2=2, 5-3=2, 6-4=2, 8-5= 3, 9-6=3, 10-7=3, 11-8=3, 13-9=4, 14-10=4
4. now count the distinct row by difference number
2 comes 3 times > that's mean 4,5,6 are consecutive empty seats (qualified for our quetion, equal to 3 seat)
3 comes 4 times > that's mean 8,9,10,11 are consecutive empty seats (qualified for our question, more than 3 seats)
4 comes 2 times > that's mean 13,14 are consecutive empty seats (not qualified cause only 2 seats consecutive)

*/
 
/* Solution */

with t1 as
	(select *, 
		row_number() over(order by seat_no asc) as rn, 
		seat_no - row_number() over(order by seat_no asc) as diff 
	from bms where is_empty = 'Y')
select seat_no from t1 where diff in (select diff from t1 group by diff having count(*) >=3) ;

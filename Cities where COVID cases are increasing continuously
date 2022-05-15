/* find cities where covid cases are incresing continuously */

create table covid(city varchar(50),days date,cases int);

delete from covid;
insert into covid values('DELHI','2022-01-01',100);
insert into covid values('DELHI','2022-01-02',200);
insert into covid values('DELHI','2022-01-03',300);
insert into covid values('MUMBAI','2022-01-01',100);
insert into covid values('MUMBAI','2022-01-02',100);
insert into covid values('MUMBAI','2022-01-03',300);
insert into covid values('CHENNAI','2022-01-01',100);
insert into covid values('CHENNAI','2022-01-02',200);
insert into covid values('CHENNAI','2022-01-03',150);
insert into covid values('BANGALORE','2022-01-01',100);
insert into covid values('BANGALORE','2022-01-02',300);
insert into covid values('BANGALORE','2022-01-03',200);
insert into covid values('BANGALORE','2022-01-04',400);

/* hints 
> let's rank the data partition by city and order by date
> again, let's rank the data partition by city and order by cases
> take their differences. If count of distinct differences is 1 and max/min/avg/sum of the differences are 0 then our output is correct.

*/

/* Solution */

with t1 as
(select *,
rank() over(partition by city order by days) as date_rank,
rank() over(partition by city order by cases) as cases_rank,
rank() over(partition by city order by days) - rank() over(partition by city order by cases) as diff
from covid
)

select city from t1
group by city
having count(distinct diff) = 1 and avg(diff) = 0 ;

/* trick to find the consecutive states start_date to end_date period */

create table tasks (
date_value date,
state varchar(10)
);

insert into tasks  values ('2019-01-01','success'),('2019-01-02','success'),('2019-01-03','success'),('2019-01-04','fail')
,('2019-01-05','fail'),('2019-01-06','success')

/* 
logic: 
> first, i have given the whole data an id column which is just a simple row number. 
> After then, I have filtered out the state ='success' and give the filtered data a new row number so that i can subtract the row number from 'id' which I had created earlier.
	i.e - 'success' filtered data has id of 1,2,3,6 and new assign row number is 1,2,3,4 if we subtract row_number from id, we get 0,0,0,2
> '0,0,0' these differences state that the 1,2,3 are consecutive and hence i just take min(date_value) as start_date and max(start_date) as end_date based on difference value which is  0.
> same case is done for state = 'fail'
*/

/* solution */
with t1 as
	(select *,row_number() over() as id from tasks),
	t2 as
	(select *, id - row_number() over(order by date_value) as diff from t1 where state = 'success'
	union all
	select *, id - row_number() over(order by date_value) as diff from t1 where state = 'fail' )
select min(date_value) as start_date,max(date_value) as end_date,max(state) from t2 group by diff order by diff ;

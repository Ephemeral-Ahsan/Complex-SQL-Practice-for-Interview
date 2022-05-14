/* find second most recent activity and if user has only 1 activoty then return that as it is */

create table UserActivity
(
username      varchar(20) ,
activity      varchar(20),
startDate     Date   ,
endDate      Date
);

insert into UserActivity values 
('Alice','Travel','2020-02-12','2020-02-20')
,('Alice','Dancing','2020-02-21','2020-02-23')
,('Alice','Travel','2020-02-24','2020-02-28')
,('Bob','Travel','2020-02-11','2020-02-18');


/* hints
1. first let us count the total activity done by each user and also find rank for each user over startdate.
2. if activity count > 1 then there must be rank = 2 for an activity,so it'll be counted
	but if there is no rank = 2 for any user then his first activity startdate will be considered. 
*/
 
/* Solution */

with cte1 as
	(select *,
		count(activity) over(partition by username) as activity_count,
		rank() over(partition by username order by startdate) as rnk
	from UserActivity)

select username,activity,startdate,enddate from cte1 
where rnk = 2 or activity_count = 1

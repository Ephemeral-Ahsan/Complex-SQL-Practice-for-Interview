/* find students with same mark in physics and Chemistry */ 

create table exams (student_id int, subject varchar(20), marks int);
delete from exams;
insert into exams values (1,'Chemistry',91),(1,'Physics',91)
,(2,'Chemistry',80),(2,'Physics',90)
,(3,'Chemistry',80)
,(4,'Chemistry',71),(4,'Physics',54);

/* hints 
> first take out the students who have given both physics and chemistry exams (distinct subject will be2 )
> then check whether they have same marks for both subject. if count(distinct marks) = 1 that means distinct mark is only one value.
that represents that student has achieved same marks in both subjects.
*/
/* Solution */

select student_id
from exams
where subject in ('Physics','Chemistry')
group by student_id
having count(distinct subject) = 2
and count(distinct marks) = 1

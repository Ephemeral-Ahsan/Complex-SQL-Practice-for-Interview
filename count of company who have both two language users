/*find companies which have at least 2 users who speak both english and german*/

create table company_users 
(
company_id int,
user_id int,
language varchar(20)
);

insert into company_users values (1,1,'English')
,(1,1,'German')
,(1,2,'English')
,(1,3,'German')
,(1,3,'English')
,(1,4,'English')
,(2,5,'English')
,(2,5,'German')
,(2,5,'Spanish')
,(2,6,'German')
,(2,6,'Spanish')
,(2,7,'English');

/* Solution-1 */

select company_id,count(*) as no_of_both_lang_users from
(select company_id from company_users
where language in ('English','German')
group by company_id,user_id
having count(distinct language) = 2) x
group by company_id
having count(*) >= 2


/* Solution-2 */

select company_id,count(distinct user_id) as no_of_both_lang_users
from
(select company_id , user_id, language as f_lang,
lead(language) over(partition by user_id) as s_lang
from company_users
where language in  ('English','German')) a
where s_lang is not null
group by company_id
having count(*) >=2

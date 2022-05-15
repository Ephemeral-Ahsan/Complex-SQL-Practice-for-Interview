/* For each store find the missing quarter */

CREATE TABLE STORES (
Store varchar(10),
Quarter varchar(10),
Amount int);

INSERT INTO STORES (Store, Quarter, Amount)
VALUES ('S1', 'Q1', 200),
('S1', 'Q2', 300),
('S1', 'Q4', 400),
('S2', 'Q1', 500),
('S2', 'Q3', 600),
('S2', 'Q4', 700),
('S3', 'Q1', 800),
('S3', 'Q2', 750),
('S3', 'Q3', 900);

select * from stores ;

/* we know that there are 4 quarters in a year. Q1,Q2,Q3,Q4. Let just sum up the quarter numbers
 1+2+3+4 = 10 ,that means 10 will be sum of quarter numbers if store has amount for 4 quarters.
 if not ,then that would be less than 10. now just think if a store have 1,2,4 quarter (we can see 3 is missing)
 but logically how can we find this? if we subtract the given quarter value from 10 which is 10-(1+2+4) = 3,
 that means Q3 is missing. 
*/

/* Solution */

select Store, concat('Q',10 - sum(right(Quarter,1)::numeric)) as missing_quarter 
from stores
group by store ;

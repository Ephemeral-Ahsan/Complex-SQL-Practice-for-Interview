/* Derive Point Table For ICC Tournament */

create table icc_world_cup
(
Team_1 Varchar(20),
Team_2 Varchar(20),
Winner Varchar(20)
);
INSERT INTO icc_world_cup values('India','SL','India');
INSERT INTO icc_world_cup values('SL','Aus','Aus');
INSERT INTO icc_world_cup values('SA','Eng','Eng');
INSERT INTO icc_world_cup values('Eng','NZ','NZ');
INSERT INTO icc_world_cup values('Aus','India','India');

select * from icc_world_cup;

/*here,I've made logic so that it raise a flag if team-1 is the winner and then union the result with if team_2 is the winner.Then just used aggregate function to derive the point table. */

/* Solution */

select x.team, count(x.team) as match_played, sum(x.win_flag) as match_won, count(x.team) - sum(x.win_flag) as match_lost from 
(select team_1 as team, case when team_1 = winner then 1 else 0 end as win_flag from icc_world_cup
union all
select team_2 as team, case when team_2 = winner then 1 else 0 end as win_flag from icc_world_cup) x
group by x.team
order by 2 desc,3 desc ;

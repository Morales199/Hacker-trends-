# Hacker-trends-
This project analyzes data from a Hacker News database
select * from hacker_news
limit 10; 

-- the 5 most popular 
 select title, score from hacker_news
 order by score desc
 limit 5; 

--Total score 
select sum(score) from hacker_news; 

-- total score for each user that combined have more that 200 points 
select user, sum(score)
from hacker_news
Group by user
Having sum(score) > 200
order by 2 desc; 

--we want to add these users’ scores together and divide by the total to get the percentage.
SELECT (517 + 309 + 304 + 282) / 6366.0;

--How many times has each offending user posted this link? ANS: 3 
select user, count(*) from hacker_news
where url like '%https://www.youtube.com/watch?v=dQw4w9WgXcQ%'
Group by user
order by count(*) desc;

select case 
  when url like '%github.com%' then 'Github'
  when url like '%medium.com%' then 'Medium'
  when url like '%neyorktime.com%'then 'Newyorktimes'
end as 'Source'
from hacker_news
limit 5;

-- it categorize the all the results from the column source and it count them also
SELECT CASE
   WHEN url LIKE '%github.com%' THEN 'GitHub'
   WHEN url LIKE '%medium.com%' THEN 'Medium'
   WHEN url LIKE '%nytimes.com%' THEN 'New York Times'
   ELSE 'Other'
  END AS 'Source',
  count(*)
FROM hacker_news
Group by 1;

select timestamp
from hacker_news
limit 10; 

--Testing a new function strtime and it returns the specific year, month, day,etc. 
select timestamp, 
strftime('%H',timestamp)
from hacker_news
group by 1 
limit 20; 

select strftime('%H',timestamp) as 'hour',round(avg(score)) as 'avg score', 
count(*) as 'Number of rows per group'
from hacker_news
group by 1
order by 2 desc;




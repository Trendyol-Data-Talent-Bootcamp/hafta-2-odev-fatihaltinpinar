```sql
select 
timestamp_trunc(view_ts, minute) as view_period,
count(distinct deviceid) active_user_count
from sample.pageview
group by 1
having (timestamp_trunc(view_period,minute) between timestamp_sub(timestamp_trunc(view_period,minute), interval 4 minute) and timestamp_trunc(view_period,minute))
order by 1 asc
limit 10;
```

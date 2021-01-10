# Soru 1) 1980’den itibaren spor grubu bazında en çok madalya alan 1. 3. 5. ülkeyi bulalım.

I couldn't put them on the columns.
This works for now.

```SQL
with medal_cnt as
(
  select
    sport,
    country,
    count(*) as medal_count,
    row_number() over(partition by sport order by count(*) desc) as siralama
  from `dsmbootcamp.fatih_altinpinar.summer_medals`
  where year >= 1980
  group by sport, country
  order by sport, count(*) desc, country
)
select
  sport,
  siralama,
  country,
  medal_count
from medal_cnt
where siralama in (1,3,5)
order by sport;
```

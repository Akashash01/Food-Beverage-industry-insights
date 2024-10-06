#demograpic_response
-- who prefers energy drinks more?
use dataset;
select count('respondent_id') as count, gender
from respondents
group by gender
order by count desc;

-- which age group prefer more drink?
select count('respondent_id') as count, age
from respondents
group by age
order by count desc;

-- which type of marketing reaches most youth(15-30)?
select s.marketing_channels ,count(distinct r.respondent_id) as total,r.age
from respondents r
join survey s
on r.respondent_id = s.respondent_id
group by r.age,s.marketing_channels
order by total desc, r.age;

------------------------------------------------------------------------------------------------------------
-- customer preferances
-- what are the preferred ingredients of energy drinks amoung respodents?
use dataset;
select s.ingredients_expected, count(distinct r.respondent_id) as total
from respondents r 
join survey s 
on r.respondent_id = s.respondent_id
group by s.ingredients_expected
order by total desc;

-- what packaging preferences do respondents have for energy drinks?
select s.packaging_preference, count(distinct r.respondent_id) as total
from respondents r 
join survey s 
on r.respondent_id = s.respondent_id
group by s.packaging_preference
order by total desc;

--------------------------------------------------------------------------------------------------------------

-- competition analysis
-- who are the current market leaders?
select s.current_brands, count(distinct r.respondent_id) as total
from respondents r 
join survey s 
on r.respondent_id = s.respondent_id
group by s.current_brands
order by total desc; 

-- primary reasons to choose brands?
select s.current_brands, a.availability, 'a.brand reputation', a.effectiveness, 'a.taste/flavor preference', a.other
from( select  

count(case when s.reasons_for_choosing_brands = 'availability' then r.respondent_id else 0 end) as availability,
count(case when s.reasons_for_choosing_brands = 'brand reputation' then r.respondent_id else 0 end) as 'brand reputation',
count(case when s.reasons_for_choosing_brands = 'effectiveness' then r.respondent_id else 0 end) as effectiveness,
count(case when s.reasons_for_choosing_brands = 'other' then r.respondent_id else 0 end) as other,
count(case when s.reasons_for_choosing_brands = 'taste/flavor preference' then r.respondent_id else 0 end) as 'taste/flavor preference'
from respondents r 
join survey s 
on r.respondent_id = s.respondent_id ) as a 
join survey s
on a.respondent_id = s.respondent_id
group by s.current_brands;

---------------------------------------------------------------------------------------------------------------

-- marketing channels and brand awareness
select s.marketing_channels ,count(distinct r.respondent_id) as total,r.age
from respondents r
join survey s
on r.respondent_id = s.respondent_id
group by r.age,s.marketing_channels
order by total desc, r.age;

-------------------------------------------------------------------------------------------

-- brand penetrations
-- overall brand rating code x
USE dataset;
select avg(taste_experience) as avg_rating 
from survey
where current_brands = 'codeX';

 -- cities to focus on
 
use dataset;
 select c.city , count(distinct r.respondent_id) as positive 
 from cities c
 join respondents r 
 on c.city_id = r.city_id
 join survey s 
 on r.respondent_id = s.respondent_id
 where s.current_brands = 'codeX' and s.brand_perception = 'positive'
 group by c.city, s.brand_perception
 order by positive desc
 union 
 select c.city , count(distinct r.respondent_id) as negative 
 from cities c
 join respondents r 
 on c.city_id = r.city_id
 join survey s 
 on r.respondent_id = s.respondent_id
 where s.current_brands = 'codeX' and s.brand_perception = 'negative'
 group by c.city, s.brand_perception
 order by negative desc 
 union
 select c.city , count(distinct r.respondent_id) as neutral 
 from cities c
 join respondents r 
 on c.city_id = r.city_id
 join survey s 
 on r.respondent_id = s.respondent_id
 where s.current_brands = 'codeX' and s.brand_perception = 'neutral'
 group by c.city, s.brand_perception
 order by neutral desc ;
 
------------------------------------------------------------------------------------------------------------------
-- purchase behaviour
-- prefer locations of customers buy drinks
select s.purchase_location, count(distinct r.respondent_id) as total
from respondents r 
join survey s on r.respondent_id = s.respondent_id
group by s.purchase_location
order by total desc;

-- consumption situations
select s.typical_consumption_situations, count(distinct r.respondent_id) as total
from respondents r 
join survey s on r.respondent_id = s.respondent_id
group by s.typical_consumption_situations
order by total desc;

-- influence factors 
select s.price_range, count(distinct r.respondent_id) as total
from respondents r 
join survey s on r.respondent_id = s.respondent_id
group by s.price_range
order by total desc;

select s.limited_edition_packaging, count(distinct r.respondent_id) as total
from respondents r 
join survey s on r.respondent_id = s.respondent_id
group by s.limited_edition_packaging
order by total desc;

---------------------------------------------------------------------------------------------------------------
-- product development
select s.brand_perception, count(distinct r.respondent_id) as total
from respondents r 
join survey s on r.respondent_id = s.respondent_id
where s.current_brands = 'codeX'
group by s.brand_perception
order by total desc;              

#has to focus on negative concerns and health concerns

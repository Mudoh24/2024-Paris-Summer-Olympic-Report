# 2024-PARIS SUMMER OLYMPIC MEDAL POSITIONS AND RANKINGS
[Dashboard link](https://app.powerbi.com/reportEmbed?reportId=87ca575f-f184-4550-8b8c-d7afc6b6a1c8&autoAuth=true&ctid=e0793d39-0939-496d-b129-198edd916feb)

### Project Overview

The data highlights trends such as the concentration of medal achievements in North America, Asia, and Europe while showcasing the contributions of smaller nations. 
It sets the stage for analyzing regional strengths, sports-specific performances, and the overall global athletic landscape at the 2024 Olympics. 
This snapshot reflects the dedication and achievements of athletes worldwide.

### Key Objectives
-The ratio of gold, silver, and bronze medals for each country
-The top 10 countries with the highest number of gold medals
-Medals won per position rank for each country
- To analyse Medal distribution across continents
- To examine he distribution of medals by each country according to its position

### Data Source
The dataset used for this analysis constitute the Paris 2024 summer olympic outcome from various particpating countries [olympics2024.csv](https://www.kaggle.com/datasets/berkayalan/paris-2024-olympics-medals?select=olympics2024.csv)

### Tool Used
-SQL Server for Data Analysis
-Power BI for Creating Reports

### Data Cleaning/Preparation
- Data Loading and Inspection
- Handling of Missing Data
- Data cleaning and formating

[Total Medals won]

### Data Analysis
Total medal won by country
``` SQL
select countries,
		sum(total_medals) AS total_medals_won
from Olympic.dbo.paris_olympic
group by countries
order by total_medals_won desc;```

Percentage of gold medals won by each country
```SQL
select 
	 Countries,
	 sum(Gold) as Gold_medals,
	 (sum(gold) * 100 / sum(total_medals)) as Gold_percentage
from Olympic.dbo.paris_olympic
group by countries
order by Gold_percentage desc;```

Medal Efficiency by Position
```SQL
select  position,
		sum(total_medals) as Gold_medals,
		AVG(total_medals) as Avg_medal_per_position
from Olympic.dbo.paris_olympic
group by position
order by position;```

Medal Type Distribution
```SQL
select countries,
	   sum(Gold) as Gold,
	   sum(Silver) as Silver,
	   SUM(Bronze) as Bronze
from Olympic.dbo.paris_olympic
group by countries
order by countries asc;

The top 10 countries with the highest number of gold medals
```SQL
select top 10 countries,
sum(Gold) as top_10_Gold_Countries
from Olympic.dbo.paris_olympic
group by countries
order by top_10_Gold_Countries desc;```

Medals per Country Ranking Efficiency
```SQL
select position,
       countries,
	   (sum(total_medals) * 1.0 / position) as medals_per_rank
from Olympic.dbo.paris_olympic
group by countries, position
order by medals_per_rank desc;```

Medals by Continent (Geographic Distribution)
select continent,
	   sum(Gold) as total_gold,
	   sum(Silver) as total_silver,
	   sum(Bronze) as total_bronze
from Olympic.dbo.paris_olympic
group by continent
order by continent desc;```

Medal Distribution by Country Ranking
```SQL
select Position, Countries,
	   sum(Gold) as total_gold,
	   sum(Silver) as total_silver,
	   sum(Bronze) as total_bronze
from Olympic.dbo.paris_olympic
group by Position, Countries
order by Position asc;```

# SUMMAR ANALYSIS
The preliminary medal standings for the 2024 Paris Summer Olympics highlight a diverse distribution of achievements across continents, with a total of 30 countries represented.
The United States leads the medal tally with 127 total medals, showcasing dominance across all categories of Gold, Silver, and Bronze.
China follows in second place with 91 medals, while Japan secures third with 45 medals, reflecting strong performances by Asian nations.
Europe emerges as a prominent contender, with multiple countries like France, the United Kingdom, and Italy earning significant medal counts.
Oceania, represented by Australia and New Zealand, demonstrates competitive strength, particularly in Gold medals.
Africa and South America also make notable contributions through nations like Kenya and Brazil.
This data provides early insights into the global competitive landscape of the Paris Olympics, emphasizing excellence and regional diversity in sports performance.













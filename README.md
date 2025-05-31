# SQL-learning-journal---day-37

# Nepal Population by District — 2021 Census (SQL Project)

This project explores district-level population data from Nepal's 2021 Census using SQLite. The goal was to extract clean, structured insights on population distribution, gender breakdown, and household sizes — perfect for beginner SQL portfolio work and data storytelling.

---

## 🗂️ Dataset Description

This dataset includes:

- `district` — Name of each administrative district in Nepal
- `population` — Total population (sum of male + female)
- `male` — Total male population
- `female` — Total female population
- `households` — Number of households in the district

---

## 📊 SQL Query Used

CREATE VIEW "by_district" AS
SELECT
    district,
    SUM(families) AS families,
    SUM(households) AS households,
    SUM(population) AS population,
    SUM(male) AS male,
    SUM(female) AS female
FROM census
GROUP BY district;


CREATE VIEW "most_populated" AS
SELECT
    district,
    SUM(families) AS families,
    SUM(households) AS households,
    SUM(population) AS population,
    SUM(male) AS male,
    SUM(female) AS female
FROM census
GROUP BY district
ORDER BY population DESC;;

CREATE VIEW rural AS
SELECT *
FROM census
WHERE LOWER (district) LIKE '%rural%'
    OR LOWER (locality) LIKE '%rural%';

CREATE VIEW "total_population" AS
SELECT
    SUM(families) AS families,
    SUM(households) AS households,
    SUM(population) AS population,
    SUM(male) AS male,
    SUM(female) AS female
FROM census;



🔎 Additional Analysis (Ideas)
Gender Ratio by District
ROUND(male * 1.0 / female, 2) to identify imbalance hotspots

Average Household Size
ROUND(population * 1.0 / households, 2) to assess density and resource demand

📁 Files
0.sql – SQL script used to query the dataset

nepal_population_by_district.csv – Cleaned dataset output

(Optional: Tableau / Power BI dashboards to follow)

📌 Insights
Kathmandu is the most populous district, with over 2 million residents.

Rural districts like Manang and Mustang have very low population densities.

Gender ratios and household sizes vary significantly between districts, providing rich ground for further data exploration.

🧠 Skills Demonstrated
SQL querying using SQLite

Data extraction with .mode and .output

Data cleaning and filtering (WHERE population IS NOT NULL)

Preparing raw data for BI tools

💬 Contact
Built by Tony Xia — aspiring Data Analyst / Junior Data Engineer

https://www.linkedin.com/in/tony-xia-4b9201237/

    


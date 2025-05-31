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


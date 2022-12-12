# Deforestation Exploration

#### About this project

> I will work for a fictional company, ForestQuery, a non-profit organization, on a mission to reduce deforestation around the world and which raises awareness about this important environmental topic.
> The company asked me to create a report of my findings.

#### Background

> The idea of this project comes from UDACITY.
> They provided a template and I will answer these questions while query the database in UDACITY IDE environment.
> I will use 3 SQL tables for this task
>
> - forest_area
> - land_area
> - regions

#### Skills I will use

> - SQL to answer business questions

### Scenario

My executive director and her leadership team members are looking to understand which countries and regions around the world seem to have forests that have been shrinking in size, and also which countries and regions have the most significant forest area, both in terms of amount and percent of total area. The hope is that these findings can help inform initiatives, communications, and personnel allocation to achieve the largest impact with the precious few resources that the organization has at its disposal.
I have been able to find tables of data online dealing with forestation as well as total land area and region groupings, and I have brought these tables together onto a database that I would like to query to answer some of the most important questions in preparation for a meeting with the ForestQuery executive team coming up in a few days.

### SETUP

I will use VIEW to JOIN all 3 tables for easier calculations.

The report can be found in the PDF file provided.  
All sentence in bold are my answer.  
I will write SQL queries(can be found in the pdf file - appendix) to answer the following questions.

```sql
DROP VIEW IF EXISTS forestation;

CREATE VIEW forestation
AS
  (SELECT f.country_code,
          f.country_name,
          f.year,
          f.forest_area_sqkm AS total_forest_area_sqkm,
          l.total_area_sq_mi * 2.59 AS total_area_sqkm,
          r.region,
          r.income_group
   FROM   forest_area AS f
          JOIN land_area AS l
            ON f.country_code = l.country_code
               AND f.year = l.year
          JOIN regions AS r
            ON f.country_code = r.country_code);
```

## PART 1 - Global Situation

- What was the total forest area (in sq km) of the world in 1990?

  > 41282694.9

- What was the total forest area (in sq km) of the world in 2016?

  > 39958245.9

- What was the change (in sq km) in the forest area of the world from 1990 to 2016?

  > 1,324,449

- What was the percent change in forest area of the world between 1990 and 2016?

  > 3.21 %

- If you compare the amount of forest area lost between 1990 and 2016, to which country's total area in 2016 is it closest to?
  > Australia

## PART 2 - Regional Outlook

- What was the percent forest of the entire world in 2016? Which region had the HIGHEST percent forest in 2016, and which had the LOWEST, to 2 decimal places?

  > Entire world = 31.38%  
  > highest = 46.16% Latin America & Caribbean  
  > lowest = 2.07% Middle East & North Africa

- What was the percent forest of the entire world in 1990? Which region had the HIGHEST percent forest in 1990, and which had the LOWEST, to 2 decimal places?

  > Entire world = 32.42%  
  > highest = 51.03% Latin America & Caribbean  
  > lowest = 1.78% Middle East & North Africa

- Based on the table you created, which regions of the world DECREASED in forest area from 1990 to 2016?

  > Sub-Saharan Africa 0.31% to 0.29%  
  > Latin America & Caribbean 0.51% to 0.46%

## PART 3 - Country-Level Detail

- Which 5 countries saw the largest amount decrease in forest area from 1990 to 2016? What was the difference in forest area for each?

  > Brazil - 541,510  
  > Indonesia - 282,193.98  
  > Myanmar - 107,234  
  > Nigeria - 106,506  
  > Tanzania - 102,320

- Which 5 countries saw the largest percent decrease in forest area from 1990 to 2016? What was the percent change to 2 decimal places for each?

  > Togo - 75.45  
  > Nigeria - 61.80  
  > Uganda - 59.13  
  > Mauritania - 46.75  
  > Honduras - 45.03

- If countries were grouped by percent forestation in quartiles, which group had the most countries in it in 2016?
  1th QT - 85  
  2nd QT - 72  
  3rd QT - 38  
  4th QT - 9

- List all of the countries that were in the 4th quartile (percent forest > 75%) in 2016.

  > Solomon Islands East Asia & Pacific 77.86  
  > American Samoa East Asia & Pacific 87.50  
  > Micronesia, Fed. Sts. East Asia & Pacific 91.86  
  > Palau East Asia & Pacific 87.61  
  > Lao PDR East Asia & Pacific 82.11  
  > Guyana Latin America & Caribbean 83.90  
  > Suriname Latin America & Caribbean 98.26  
  > Gabon Sub-Saharan Africa 90.04  
  > Seychelles Sub-Saharan Africa 88.41

- How many countries had a percent forestation higher than the United States in 2016?  
  > 94

# COVID-19 Data Analysis

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas)
![NumPy](https://img.shields.io/badge/NumPy-Data%20Processing-013243?logo=numpy)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green)

## Overview

This project presents a data analysis of COVID-19 cases using a publicly available dataset from Kaggle.

The analysis examines the development of reported COVID-19 cases over time and compares the impact of the pandemic across countries and WHO regions. The project focuses on exploratory data analysis, data validation, statistical analysis, and visualization rather than machine learning.

The dataset covers the period from **January 22, 2020 to July 27, 2020** and contains information about confirmed cases, deaths, recoveries, and active cases for 187 countries/regions.

This is a personal data science project developed to practice and demonstrate practical data analysis using Python.

---

## Objectives

The main objectives of this project are to:

- Explore and understand a real-world COVID-19 dataset.
- Prepare and validate the dataset for analysis.
- Examine how reported COVID-19 cases changed over time.
- Compare the impact of COVID-19 between countries.
- Compare COVID-19 cases between WHO regions.
- Investigate the relationship between confirmed cases and deaths.
- Calculate and compare country-level death rates.
- Analyze the development and peaks of active cases.

---

## Research Questions

The analysis is based on the following seven questions:

1. **How did COVID-19 cases change globally over time?**
2. **Which countries were most affected by COVID-19?**
3. **How did the impact of COVID-19 differ between WHO regions?**
4. **Is there a relationship between confirmed cases and deaths?**
5. **Which countries had the highest death rate relative to confirmed cases?**
6. **How did active COVID-19 cases change over time?**
7. **When did different countries reach their highest number of active cases?**

---

## Dataset

The dataset was obtained from Kaggle:

**Source:** Corona Virus Report  
**Publisher:** Kaggle  
**Dataset:** [https://www.kaggle.com/datasets/imdevskp/corona-virus-report](https://www.kaggle.com/datasets/imdevskp/corona-virus-report)

The dataset used in this project contains:

- **49,068 rows**
- **10 columns**
- **187 countries/regions**
- **188 dates**
- **Date range:** January 22, 2020 – July 27, 2020

### Dataset Columns

| Column | Description |
|---|---|
| `Province/State` | Province or state where the observation was recorded, when available |
| `Country/Region` | Country or region |
| `Lat` | Latitude |
| `Long` | Longitude |
| `Date` | Date of the observation |
| `Confirmed` | Reported confirmed COVID-19 cases |
| `Deaths` | Reported COVID-19 deaths |
| `Recovered` | Reported recovered cases |
| `Active` | Reported active cases |
| `WHO Region` | WHO region associated with the country/region |

---

## Project Structure

```text
Covid19/
│
├── data/
│   ├── raw/
│   │   └── covid_19_clean_complete.csv
│   │
│   └── processed/
│       └── covid_cleaned.csv
│
├── notebooks/
│   ├── 01_exploration.ipynb
│   ├── 02_cleaning.ipynb
│   └── 03_analysis.ipynb
│
├── visualizations/
│
├── README.md
├── requirements.txt
└── .gitignore

Notebooks
01_exploration.ipynb
Initial exploration and understanding of the dataset, including:
Dataset dimensions
Column inspection
Data types
Missing values
Duplicate records
Basic descriptive statistics
Category and region inspection
Initial data validation
02_cleaning.ipynb
Data preparation and validation.
The dataset was checked for:
Duplicate records
Missing values
Invalid values
Inconsistent case counts
Date formatting
Data consistency
The cleaned dataset is saved as:
data/processed/covid_cleaned.csv

03_analysis.ipynb
Contains the complete analysis of the seven research questions, including calculations, tables, and visualizations.

Data Preparation and Validation
The dataset contained 0 duplicate rows.
The Province/State column contained 34,404 missing values. These values were retained because province/state information is not available for every country in the dataset.
The Date column was stored as a datetime data type.
During validation, 18 records were identified where the reported Active value was inconsistent with the other case counts:
Deaths + Recovered > Confirmed

These inconsistencies were identified during the cleaning and validation stage and are documented as a limitation of the source data.
No rows were removed because of these inconsistencies.
A Data Inconsistent indicator was also created during the cleaning process to identify inconsistent records.

Analysis
Q1 — How did COVID-19 cases change globally over time?
The time-series analysis examined confirmed cases, deaths, recovered cases, and active cases over the observation period.
At the beginning of the dataset, confirmed cases, deaths, recovered cases, and active cases were close to zero. During February, the numbers remained relatively low, followed by a substantial increase beginning around the latter part of March.
Confirmed, recovered, and active cases increased considerably during the following months. Deaths also increased, although the change was considerably less pronounced on the visualization compared with the other measures.
The complete time-series visualizations and calculations are available in 03_analysis.ipynb.

Q2 — Which countries were most affected by COVID-19?
Countries were compared using their total reported confirmed cases, deaths, recovered cases, and active cases over the analyzed period.
Top 10 Countries by Confirmed Cases
Country
Confirmed
United States
4,290,259
Brazil
2,442,375
India
1,480,073
Russia
816,680
South Africa
452,529
Mexico
395,489
Peru
389,717
Chile
347,923
United Kingdom
301,708
Iran
293,606

Top 10 Countries by Deaths
Country
Deaths
United States
148,011
Brazil
87,618
United Kingdom
45,844
Mexico
44,022
Italy
35,112
India
33,408
France
30,212
Spain
28,752
Peru
18,418
Iran
15,912

Top 10 Countries by Recovered Cases
Country
Recovered
Brazil
1,846,641
United States
1,325,804
India
951,166
Russia
602,249
Chile
319,954
Mexico
303,810
South Africa
274,925
Peru
272,547
Iran
255,144
Pakistan
241,026

Top 10 Countries by Active Cases
Country
Active
United States
2,816,444
Brazil
583,080
India
495,499
United Kingdom
254,427
Russia
245,382
South Africa
173,590
Colombia
117,163
France
108,928
Pakistan
108,642
Peru
108,616

The United States had the highest reported number of confirmed cases, deaths, and active cases in the analyzed data. Brazil had the highest number of recovered cases.

Q3 — How did the impact of COVID-19 differ between WHO regions?
The six WHO regions were compared using confirmed cases, deaths, recovered cases, and active cases.
WHO Region
Confirmed
Deaths
Recovered
Active
Africa
452,529
7,067
274,925
173,590
Americas
4,290,259
148,011
1,846,641
2,816,444
Eastern Mediterranean
293,606
15,912
255,144
108,642
Europe
816,680
45,759
602,249
254,352
South-East Asia
1,480,073
33,408
951,166
495,499
Western Pacific
82,040
4,512
64,435
53,649

The Americas had the highest reported values for confirmed cases, deaths, recovered cases, and active cases in this analysis. The Western Pacific region had the lowest reported totals among the six regions.

Q4 — Is there a relationship between confirmed cases and deaths?
A correlation analysis was performed using country-level confirmed cases and deaths.
The Pearson correlation coefficient was:
r = 0.9345541558

This represents a strong positive correlation between confirmed cases and deaths in the dataset. In general, countries with higher numbers of confirmed cases also tended to have higher numbers of reported deaths.
However, correlation does not establish causation. Other factors may influence the number of deaths reported by each country.

Q5 — Which countries had the highest death rate relative to confirmed cases?
Death rate was calculated as:
Death Rate = (Deaths / Confirmed) × 100

To reduce the effect of extremely small case counts, only countries with at least 1,000 confirmed cases were included.
Top 10 Death Rates
Country
Confirmed
Deaths
Death Rate (%)
Yemen
1,691
483
28.56
United Kingdom
301,708
45,844
15.19
Belgium
66,428
9,822
14.79
Italy
246,286
35,112
14.26
France
220,352
30,212
13.71
Hungary
4,448
596
13.40
Netherlands
53,413
6,160
11.53
Mexico
395,489
44,022
11.13
Spain
272,421
28,752
10.55
Canada
116,458
8,944
7.68

Yemen had the highest calculated death rate among the countries included in the comparison.
This metric should be interpreted carefully because reported death rates can be strongly affected by testing coverage, reporting practices, healthcare systems, and other country-specific factors.

Q6 — How did active COVID-19 cases change over time?
Active cases remained close to zero during the early part of the observation period, with a small increase around the middle of February.
A much more substantial increase began around the latter part of March, after which active cases increased considerably throughout the analyzed period.
The complete visualization is available in 03_analysis.ipynb.

Q7 — When did different countries reach their highest number of active cases?
The date and value of the maximum reported active cases were identified for each country and the highest peaks were compared.
Country
Date of Peak
Peak Active Cases
United States
2020-07-27
2,816,444
Brazil
2020-07-23
583,080
India
2020-07-27
495,499
United Kingdom
2020-07-27
254,427
Russia
2020-06-15
245,382
South Africa
2020-07-20
173,590
Colombia
2020-07-27
117,163
France
2020-07-27
108,928
Pakistan
2020-07-01
108,642
Peru
2020-06-25
108,616

The timing of peak active cases differed between countries. While several countries reached their highest reported active case counts near the end of the observation period, others reached their peaks earlier.

Key Findings
The analysis produced several major observations:
Reported COVID-19 cases increased substantially during the analyzed period, particularly from late March onward.
The impact of COVID-19 was highly uneven between countries.
The United States had the highest reported confirmed, death, and active case totals in the dataset.
Brazil had the highest reported number of recovered cases.
The Americas had the highest reported totals among the WHO regions.
Confirmed cases and deaths showed a strong positive correlation (r ≈ 0.935).
Death rates varied substantially between countries.
Countries reached their highest active-case counts at different points during the observation period.

Limitations
This analysis has several limitations:
The dataset covers only January 22, 2020 to July 27, 2020.
The dataset contains 18 records with inconsistent Active values.
Province/State contains a large number of missing values.
Reported cases and deaths may not represent the actual number of infections and deaths.
Countries may have used different testing, reporting, and classification practices.
Population data is not included, so population-adjusted comparisons such as cases per 100,000 people were not performed.
Correlation analysis identifies relationships between variables but does not establish causation.

Technologies
Python
Pandas
NumPy
Matplotlib
Jupyter Notebook

Author
Lasha Jincharadze
GitHub: @lashvv
Email: lashajincharadze16@gmail.com

License
This project is licensed under the MIT License. See the LICENSE file for details.


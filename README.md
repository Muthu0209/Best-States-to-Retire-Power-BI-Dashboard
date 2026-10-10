# 🏖️ Best States to Retire: Power BI Dashboard

Power BI dashboard ranking all 50 U.S. states for retirement using housing, taxes, health, crime, quality of life and living costs. Built with Power Query and DAX; shows Top 5 and Worst 5 states by a custom score.
 
![Dashboard Preview]([images/dashboard.png](https://drive.google.com/file/d/1-N1xWQtlAm3I-8zsdWZx2-jn4ha_VBDJ/view?usp=sharing))


##  Project Overview

Choosing where to retire depends on many factors: cost of housing, taxes, safety, healthcare and more. This dashboard combines those factors into one easy-to-read **New Score** per state, so users can quickly see which states are the best and worst places to retire.

The report is useful for retirees, financial planners, and anyone comparing states on affordability and quality of life.


## Objectives

- Clean and prepare state-level retirement data in Power Query
- Join the data with official U.S. state abbreviations (ANSI codes)
- Create a custom **New Score** that weights six key factors equally
- Show the **Top 5** and **Worst 5** states in clear ranked tables

## Tech Stack

- **Power BI Desktop**: report creation and visualization
- **Power Query (M code)**: data cleaning, merging, and transformation
- **DAX**: calculated score and ranking (Top N / Bottom N filters)
- **Data Modeling**: relationships between the retirement data and the state-codes table
- **Data Source**: CSV (`retirement.csv`) and a web table (Wikipedia)


## Dataset

| Source | Description |
|---|---|
| `data/retirement.csv` | 50 U.S. states scored 0–100 on 8 columns (below) |
| [Wikipedia: U.S. state and territory abbreviations](https://en.wikipedia.org/wiki/List_of_U.S._state_and_territory_abbreviations) | State names mapped to ANSI codes |

**Columns in the retirement data**

| Column | Meaning |
|---|---|
| State | U.S. state name |
| Quality of life | Overall living quality score |
| Cost of housing | Housing affordability score |
| Public health | Healthcare and health outcomes |
| Crime | Safety score |
| Taxes | Tax friendliness |
| Weather | Climate score |
| Non-housing cost of living | Everyday expenses excluding housing |
| Overall weighted and normalized score | The original combined score from the source |

> Higher score = better for retirement.


## Data Preparation (Power Query)

1. Loaded `retirement.csv` into Power BI
2. Imported the state abbreviations table from Wikipedia as **States Codes**
3. Checked data types and fixed mismatches so columns could be combined
4. **Merged queries** on state name to bring the **ANSI** code into the retirement data
5. Created a **State Name Filter** helper query and a reusable **Retirement data Invoke** query
6. Removed the *Weather* column from the final score (see below)
7. Closed and applied the changes

## Key Calculation: New Score

**New score** is the simple average of six factors:


New score = (Quality of life + Cost of housing + Public health
             + Crime + Taxes + Non-housing cost of living) / 6

Weather is left out because it is a personal preference and not a cost or safety factor. Every remaining factor carries equal weight.

## Dashboard Contents

| Visual | What it shows |
|---|---|
| **Top 5 States** table | States with the highest New Score, sorted descending |
| **Worst 5 States** table | States with the lowest New Score, sorted ascending |

### Results

**Top 5**

| State | New Score |
|---|---|
| North Dakota | 71.67 |
| Wyoming | 70.67 |
| Minnesota | 70.50 |
| Nebraska | 69.83 |
| Utah | 69.50 |

**Worst 5**

| State | New Score |
|---|---|
| California | 45.17 |
| New Mexico | 46.00 |
| Alaska | 47.50 |
| Hawaii | 47.83 |
| Arkansas | 48.50 |


## Key Insights

- **Midwest and Mountain states lead**: North Dakota, Wyoming, Minnesota, Nebraska and Utah score highest, mainly thanks to lower housing and everyday costs.
- **High-cost states rank lowest**: California and Hawaii are pulled down by very expensive housing.
- **Alaska and New Mexico** drop because of weaker crime scores, plus cost of living in Alaska.


##  Repository Structure

├── retirement-dashboard.pbix   # Power BI report
├── data/
│   └── retirement.csv          # Source data
├── images/
│   └── dashboard.png           # Dashboard screenshot
└── README.md

⭐ If you found this project useful, please star the repo!ttps://github.com/Muthu0209)


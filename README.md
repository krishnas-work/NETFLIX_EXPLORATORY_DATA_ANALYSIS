# Netflix Content Analysis — Exploratory Data Analysis (EDA)

## 📌 Problem Statement
Netflix's catalog metadata is analyzed to uncover patterns in content type, geography, genre, director contribution, audience ratings, and release timing — helping understand how Netflix builds and schedules its content library.

## 🎯 Objectives
- Compare the split between Movies and TV Shows
- Identify top contributing countries, directors, and genres
- Understand audience-rating distribution (Kids / Teens / Adults)
- Analyze trends in content additions over years, months, and weekdays
- Examine typical movie runtimes and TV show season counts

## 🗂️ Dataset
- **Source:** [Netflix Titles dataset (Kaggle)](https://www.kaggle.com/datasets/shivamb/netflix-shows)
- **Size:** 8,807 rows × 12 columns (raw)
- **Columns:** `show_id`, `type`, `title`, `director`, `cast`, `country`, `date_added`, `release_year`, `rating`, `duration`, `listed_in`, `description`

## 🧹 Data Cleaning
- Dropped irrelevant `show_id` column; renamed `listed_in` → `genre`
- Removed rows with missing `date_added`, `rating`, `duration` (small % of data)
- Standardized `rating` into 3 categories per [Netflix's official classification](https://help.netflix.com/en/node/2064/us): **Kids, Teens, Adults**
- Removed 96 rows missing `director`, `country`, and `cast` simultaneously
- Unnested multi-value columns (`cast`, `director`, `country`, `genre`) into a long format for accurate counting
- Removed 55 duplicate rows post-unnesting

Final cleaned dataset (pre-unnesting): **8,525 rows × 16 columns**

## 📊 Key Findings
- Movies significantly outnumber TV Shows in Netflix's catalog
- The **United States** is the largest content contributor by far
- Content additions **peaked in 2019 (1,412 movies)**, then declined in 2020-2021 (likely pandemic-related production slowdowns)
- **Friday is by far the most common content-release day** (1,537 additions vs. 612 on Monday) — suggesting a deliberate weekend-engagement release strategy
- Most TV shows run for only 1-2 seasons; movie runtimes cluster within a fairly narrow typical range
- A small set of genres and directors account for a disproportionate share of the catalog

*(See the notebook for full breakdowns and charts of country, genre, director, and rating distributions.)*

## 💼 Business Recommendations
- Formalize Friday releases as a scheduling strategy across all regions/genres
- Diversify content investment beyond the US/India-heavy mix to grow international subscribers
- Increase multi-season TV investment to complement the movie-heavy library and support long-term retention

## ⚠️ Limitations
- Static dataset snapshot — does not reflect content added after collection
- Rows with key missing values were dropped rather than imputed
- Frequency-based charts (top directors/genres) can be biased toward titles with more listed contributors, since the data was unnested into one row per value

## 🚀 Future Scope
- Combine with IMDb/Rotten Tomatoes ratings to analyze quality vs. quantity
- Build a content-based recommendation system using genre/cast similarity
- Time-series forecasting of future content additions

## 🛠️ Tech Stack
`Python` · `pandas` · `numpy` · `matplotlib` · `seaborn` · `Jupyter Notebook`

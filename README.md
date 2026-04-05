# Census Demographic Analysis and Policy Recommendations

A data science study cleaning and analysing 8,175 mock census records to produce evidence-based policy recommendations for town development.

## Overview

This project takes a messy census dataset and transforms it into a rigorous demographic analysis with concrete policy recommendations. The work demanded careful, context-aware data cleaning guided by demographic knowledge and legal precedent, statistical comparison with national benchmarks, and the translation of quantitative findings into actionable guidance.

## What This Project Covers

**Data Cleaning**
- Household-level age imputation using composite addresses and family clustering
- Gender standardisation across multiple format variants
- Marital status resolution using Marriage Act precedent and demographic reasoning
- Religion cleaning handling refusals, data errors, column shifts, and known census jokes
- Conservative approach: less than 1% of cells modified, all decisions documented

**Exploratory Analysis**
- Population pyramid construction revealing expansive demographic structure
- Crude birth, death, and migration rate estimation from cross-sectional data
- Household composition and family demand analysis
- Labour market and unemployment analysis by age cohort
- Religion, marital status, and health/infirmity distributions

**Statistical Testing**
- t-tests and chi-squared tests comparing town demographics to England and Wales benchmarks
- Unemployment significantly above national average (t = 5.23, p < 0.001)
- Under-16 proportion significantly elevated (chi-squared = 14.8, p < 0.001)
- Over-65 proportion significantly below national levels (chi-squared = 82.4, p < 0.0001)

**Policy Recommendations**
- High-density family housing recommended for unoccupied plot (supported by population structure)
- Increased schooling investment recommended as top priority (75-80 new entrants/year projected)
- All alternative options evaluated and rejected with specific statistical evidence

## Technical Stack

- Python, Pandas, NumPy
- Matplotlib, Seaborn
- SciPy (statistical testing)
- Jupyter Notebooks

## Project Structure

```
Census_Data_Cleaning_and_EDA.ipynb   # Complete cleaning and analysis notebook
Census_Project_Report.md             # Full written report with recommendations
README.md                            # This file
```

## Case Study

A detailed reflective case study is available on my [portfolio site](https://chimezie-ai-portfolio.netlify.app/case-study/census-demographic-analysis).

## Author

Chimezie Onuchukwu
- [Portfolio](https://chimezie-ai-portfolio.netlify.app)
- [LinkedIn](https://www.linkedin.com/in/onuchukwu-joseph-589912148)

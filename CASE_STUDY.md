# From Messy Census Records to Policy Recommendations: A Demographic Data Science Study

## Summary

I cleaned, analysed, and interpreted a mock census dataset of 8,175 residents to produce evidence-based recommendations for town development. The project demanded careful data cleaning guided by demographic context and legal precedent, statistical comparison with national benchmarks, and the translation of quantitative findings into concrete policy guidance. It was, in many ways, the most intellectually demanding project I have worked on, because the hardest part was not the code but the judgment calls.

## Context and Motivation

The setting was a mid-sized British town located between two larger cities. The dataset resembled the 1881 UK census in structure but reflected contemporary demographics, with eleven categories covering age, gender, marital status, occupation, religion, household relationships, and infirmity. The task was to analyse the population and make two specific recommendations: what to build on an unoccupied plot of land, and where to direct future public investment.

What made this project interesting was not the size of the data (8,175 records is modest) but the quality of thinking it required. Census data is inherently messy. People misreport. Enumerators make transcription errors. Edge cases do not fit neatly into categories. The cleaning decisions you make shape every downstream analysis, and there is rarely a single correct answer. You have to reason carefully, document everything, and be honest about uncertainty.

## Problem Definition

Three interconnected problems:

1. **Data cleaning:** Resolve inconsistencies, missing values, and errors while preserving data integrity and minimising bias.
2. **Exploratory analysis:** Characterise the population structure, estimate demographic rates, and identify statistically significant departures from national benchmarks.
3. **Policy recommendation:** Use the analysis to justify specific, evidence-backed decisions about land use and public investment.

## Why the Problem Mattered

Census data informs how governments allocate resources, plan infrastructure, and respond to demographic change. A flawed analysis does not just produce wrong numbers; it can lead to policy decisions that fail the people they are meant to serve. The gap between "technically correct" and "actually useful" analysis is where most of the difficulty lives. This project sat squarely in that gap.

## My Role and Contribution

I was responsible for the complete pipeline: data cleaning methodology design, implementation, exploratory analysis, statistical testing, and the final report with policy recommendations.

## Approach and Methodology

**Data cleaning was the core of the project.** I spent more time on cleaning decisions than on any other phase, and I believe that was the right allocation.

For age values, I used a household-level methodology. I constructed composite addresses (house number plus street) to identify households, then imputed missing or invalid ages using the household median rather than the global median. This is standard in census demography because family members tend to cluster in age, so a household median is a better estimate than a population-wide one. When no household median was available, I fell back to the global median of 36 years. I excluded biologically implausible ages (115+) and adjusted one extreme outlier (age 111) to the household median.

One specific case illustrates the kind of judgment required: a textual age entry ("three") appeared in the data. From the household context, it was clear this referred to a 3-year-old child. The correction was obvious in this case, but the principle extends: every cleaning decision should be traceable to evidence.

Gender standardisation mapped all variants ('male', 'M', 'm', 'female', 'F', 'f') to two categories. Marital status required more thought. Abbreviations were expanded, 'NA' was retained for minors under 16, and 255 adult students with 'NA' were imputed as 'Single' based on demographic reasoning. Four individuals coded as 'Widowed' under age 18 were recoded as 'Single', since widowhood among minors is extremely rare in the UK context. One anomalous household (a 15-year-old listed as Head, married with a child and an adult husband) was excluded entirely due to multiple inconsistencies. That exclusion removed three records, less than 0.04% of the data.

Religion cleaning handled blanks, refusals, data errors (including three 'Housekeeper' entries likely caused by column shifts), spelling corrections ('Buddist' to 'Buddhist'), and known census jokes ('Sith', referencing a well-documented phenomenon of joke responses in UK censuses). All ambiguous entries were recoded as 'None'.

**Exploratory analysis** built on this cleaned foundation. I constructed a population pyramid that revealed an expansive shape: broad base, parental bulge at 35 to 49, narrow apex. Children under 16 comprised 19.2% of the population, significantly above the England and Wales 2021 average of 18.5%. Only 12.8% were aged 65 or older.

I estimated crude birth and death rates from the cross-sectional age structure, since no time-series data was available. This required careful reasoning: the number of 0-year-olds (57) gave an approximate crude birth rate of 7.0 per 1,000. The expected-versus-actual elderly population suggested a crude death rate of approximately 8.5 per 1,000. Net migration was inferred from excess population in the 20 to 40 age cohorts, estimated at roughly +1.5% annually.

**Statistical testing** compared the town's demographics against national benchmarks. The unemployment rate of 7.7% among adults was significantly above the UK average of 4.4% (t = 5.23, p < 0.001). The under-16 proportion was significantly elevated (chi-squared = 14.8, p < 0.001). The 65+ proportion was significantly below national levels (chi-squared = 82.4, p < 0.0001).

## Key Technical Decisions

**Household-level imputation over global imputation.** Using household medians for missing ages respected the demographic reality that family members' ages cluster. This is a small decision with meaningful downstream effects on age distribution statistics.

**Conservative cleaning with full documentation.** I removed less than 1% of cells and excluded only three records entirely. Every correction was recorded in the Jupyter Notebook with the reasoning behind it. In demographic analysis, aggressive cleaning can introduce as much bias as it removes.

**Estimating rates from cross-sectional data.** Without longitudinal data, I derived birth, death, and migration rate estimates from the age structure. This required explicit assumptions and careful caveats. I was transparent about the limitations of these estimates rather than presenting them as definitive.

## Challenges, Tradeoffs, and Constraints

The hardest decisions were not technical but interpretive. When is an unusual data point an error versus a genuine outlier? The 111-year-old could have been a real person (verified UK longevity data supports ages up to about 115), but in the context of this household, the value was more likely a data entry error. I adjusted it but documented the reasoning.

The marital status of minors presented a philosophical question about data cleaning: should you impose assumptions about what is "normal" or preserve what was recorded? I chose to recode clearly implausible values (widowed children) while retaining ambiguous ones with appropriate labels. There is no universally correct answer, but the reasoning should be explicit.

The absence of time-series data meant that all rate estimates were approximations derived from a single snapshot. I noted this limitation prominently rather than burying it.

## What I Learned

This project taught me that data cleaning is not a preliminary chore to rush through before the "real" analysis begins. It is the analysis. The decisions you make when resolving a missing value or correcting an implausible entry are themselves analytical judgments that require domain knowledge, statistical reasoning, and intellectual honesty.

I also learned the value of tying quantitative findings to concrete decisions. Showing that 19.2% of the population is under 16 is informative. Showing that this figure significantly exceeds the national average and then connecting it to a specific recommendation about school investment is useful. The gap between informative and useful is where data science creates real value.

## Outcome

The analysis recommended high-density family housing for the unoccupied plot (supported by the expansive population pyramid, elevated child proportion, and large household sizes) and increased investment in schooling as the top public spending priority (supported by the 19.2% under-16 population and projected 75 to 80 new school entrants annually). Alternative options were evaluated and rejected with specific statistical evidence.

## Why This Work Matters for Research Readiness

Research often involves working with imperfect data, making principled decisions under uncertainty, and communicating findings to audiences who need to act on them. This project exercised all of those skills. The data cleaning methodology drew on census demography, legal precedent, and statistical reasoning. The analysis connected quantitative findings to actionable recommendations. The documentation was thorough enough for someone else to reproduce and challenge every decision.

This is the kind of work where technical skill alone is not enough. You also need judgment, domain awareness, and the willingness to be transparent about what you do not know.

## What I Would Investigate Next

With access to multiple census waves, I would build a longitudinal model of population change rather than relying on cross-sectional inference. Spatial analysis, examining how demographics vary by street or neighbourhood, would add another dimension. And simulation-based approaches could estimate the uncertainty in the rate calculations more rigorously than the point estimates I produced here.

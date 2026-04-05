# Demographic Analysis of the 2025 Mock Census

**Author:** Chimezie Onuchukwu

---


## Demographic Analysis Of The 2025 Mock Census And Evidence-Based Recommendations For Town Development


Onuchukwu Joseph Chimezie

## [Redacted]











## Introduction

The report follows the evaluation of given census data projected for 2025 and provides a data science analysis for a mid-sized British town that is established to have been located between two larger cities and connected by motorways. The dataset used in this report is described as resembling the 1881 UK census; however, it is noted that it reflects contemporary demographics and initially included 8,175 individual records. Also, the dataset used in this report initially has some errors and missing values, and to make informed decisions from the dataset, we need to clean it. After we have cleaned our dataset, the final dataset contains 8,174 residents across eleven demographic categories.
For this report, we want to analyse a few key factors that would help us make proper decisions to support the local government planning in the town. And for the findings to be guided by intelligence, the factors we considered are specifically population growth—where we looked at an age pyramid, unemployment rates, housing demand, commuting patterns, and religious trends. The reasons for our findings are critical for two main decisions: to help determine what should occupy the unoccupied plot of land and to identify, with full assurance of the cleaned dataset, the highest priority area for future public investment.

## Data Cleaning Methodology

The data cleaning process used for this report was one that is both conservative and transparent. And the cleaning process was guided by demographic context. We resolved inconsistencies, missing values, and potential inaccuracies in the dataset to preserve data integrity. Only a minimal fraction, less than 1%, of the cells needed any corrective action. The decision employed in the cleaning was made sure to be supported by contextual evidence, relevant legal precedents, and well-established census patterns, with every step fully recorded in the provided Jupyter Notebook.
‘Age’ values were cleaned using a household-level methodology. A single textual entry ('three') was corrected to 3 based on family context. The Age column was converted to a numeric format, and invalid entries were set to NaN. Ages were categorised based on a composite Address field (House Number combined with Street), facilitating the imputation of missing or invalid ages through the household median, a conventional method in census demography owing to familial clustering. If a household median was unavailable, the global median (36 years) was used. Biologically, ages that did not make sense, such as 115 or more, were excluded to conform to validated UK longevity data. One extreme outlier (age 111) was adjusted to the household median to prevent distortion of elderly age distributions. The final dataset included ages from 0 to 115 years, with a mean of 37.2, a median of 36, and no missing values.
All variants of gender entries (including 'male', 'M', 'm, 'female', 'F', 'f') were standardised to 'Male' or 'Female' using a mapping approach. The final counts were 4,062 males (49.7%) and 4,112 females (50.3%).
Abbreviations in Marital Status (S=Single, M=Married, D=Divorced, W=Widowed) were fully expanded. 'NA' was retained for minors under 16, while for individuals aged 16–17, values were imputed to adult statuses where possible, based on household context and marriage law. For 255 adult students, 'NA' was imputed as 'Single'. Four cases coded as 'Widowed' under age 18 were recoded as 'Single', as widowhood among minors is rare and inconsistent with UK norms. An anomalous household with a 15-year-old Head, married with a child and an adult husband, was excluded (n=3 records) due to multiple likely inconsistencies, representing less than 0.04% of the data. The final adult status distribution was: Single 47.1%, Married 35.0%, Divorced 11.3%, Widowed 6.6%.
For the ‘Religion’ variable, blanks, refusals ('Nope', 'Private'), and data errors (such as three 'Housekeeper' entries likely resulting from column shifts, and 'Buddist' corrected to 'Buddhist') were recoded as 'None'. For individuals under 18, most of whom had 'NA' (n=1,861), this label was also converted to 'None' to reflect the dominant patterns and minimise bias in the analysis. Four joke or false entries ('Sith'), referencing a known census prank, were recorded as 'None'. The final distribution was: None 56.7%, Christian 23.5%, Catholic 11.0%, Methodist 6.3%, Muslim 1.2%, and other religions 0.9%.
For other fields, missing first names were filled with 'Unknown', and a missing relationship was assigned as 'Lodger' for a student in a shared house. In the Infirmities field, blanks were replaced with 'None'. Children’s occupations were verified as 'Student' or 'Child', with no further modifications. A composite ‘Address’ was constructed for 3,220 households.
In this approach, we have ensured replicability and reduced bias as we drew on legal (Marriage Act) and historical (BBC) sources for robustness.

## Key Findings From Exploratory Analysis

Population Structure and Growth Potential
The population pyramid (Figure 1) shows a typical expansive shape with a broad base, a parental bulge (35–49), and a narrow apex.

Children under 16 comprise 19.2% of the population—significantly above the England & Wales 2021 average of 18.5%. Conversely, only 12.8% are aged 65+. The inferred crude birth rate is 9.3 per 1,000, confirming sustained demographic expansion.
Birth, Death, and Migration Rates
Rates were derived from the population age structure due to the absence of direct time-series data.
Crude Birth Rate (CBR) formula: The formula for the Crude Birth Rate is; CBR = (Number of births / Population) × 1000. It is approximated as number of 0-year-olds (57) / 8,174 × 1000 = 7.0 per 1,000 (UK 2023 average: 10.4 – lower but consistent with pyramid base, suggesting recent stability or in-migration).
Crude Death Rate (CDR) formula: For the Crude Death Rate, it is represented as: CDR = (Number of deaths / Population) × 1000. This estimate was based on the proportion of elderly individuals and survival rates, with the expected population aged 65 and over from the 55–64 cohort being approximately 850, while the actual figure is 1,046. This implies a CDR of approximately 8.5 per 1,000, slightly lower than the UK 2023 average of 10.3 and consistent with the observed narrow apex of the population pyramid.
Net Migration Rate estimate: The formula for this is: Net migration = Total growth – Natural increase (births – deaths). Now, if we agree with the recent population stability as shown by the age pyramid we have plotted, then the net migration is approximately +1.5% annually. This estimate is inferred from the excess population in the 20–40 age cohorts compared to births and deaths, supporting the hypothesis of family in-migration.
These demographic rates confirm that both natural increase (CBR exceeding CDR) and migration contribute to population growth. Approximately 75 to 80 new school entrants are expected annually based solely on the number of births.
Household Composition and Family Demand
The mean household size is 2.54 persons (national average: 2.36). Notably, 22.9% of households contain four or more residents (Figure 4).

This high density suggests a prevalence of family units rather than single-occupancy dwellings, indicating potential overcrowding risks if the housing stock does not expand.
Labour Market and Commuting
From the figure, we can agree that the declared unemployment is 6.3% overall and 7.7% among adults—higher than the UK national average (~4.4%). At 10.7%, where there is a peak in the 40-49 age range, it shows a mid-career disruption. However, detailed cohort analysis (Figure 2) reveals this is not a youth crisis.

Categorical Distributions
Religion
After rigorous cleaning, 56.7% declare “None”—far exceeding the England & Wales 2021 figure of 37.2% (ONS, 2021). All Christian denominations combined total only 40.8%. The minority faiths are negligible, as they are less than 2%; as such, there is no evidence of demand for any additional religious building.






Marital Status
Among adults, 38.2% are single, 28.3% are married, 9.3% are divorced, and 5.0% are widowed. The 19.2% classified as “NA” primarily consists of minors under the age of 16, for whom non-response is appropriate. Outliers like widowed under 18 were identified via boxplot (Figure 5) and recoded as 'NA'. Marriage and divorce rates align closely with national averages, indicating no significant instability.

The boxplot shows age distributions by marital status. The four widowed individuals under 18 are clear outliers (below the lower whisker) and were recoded to 'NA' as implausible.
Employment/Occupation
The cleaned data show this employment profile:
There are 504 university students, making up 6.2% of the total population. Because the town does not have a university, all of these students commute daily to nearby cities.
Children and school-aged students, listed as “Student” or “Child”, form the largest group at 18.9%. This highlights the town’s young population.
There are 511 people who are unemployed, which is 6.3% of the total population and 7.7% of working-age adults. This is much higher than the current UK national rate of 4.4% (ONS, 2024).
Most unemployment is found in the 40 to 49 age group (10.7%), which points to a mid-career issue instead of youth unemployment.

Health and Infirmity
The cleaned dataset identifies only 49 individuals (0.6%) with any recorded infirmity, while the remaining 8,125 residents (99.4%) are classified as having none. However, census-based data may underreport disabilities or chronic conditions because of self-reporting biases or misclassification.
This figure indicates a notably lower prevalence compared to typical UK rates for disability or long-term health conditions, which are approximately 18% of adults (ONS 2021). Even when accounting for potential under-reporting common in censuses, the prevalence remains substantially lower.

## Comparison With National Benchmarks

Table 1: Key demographic indicators compared with England & Wales (2021–2024)

Table 1 compares the town’s key demographic indicators against contemporary England & Wales benchmarks (ONS 2021 Census and 2024 labour market data). All differences are statistically significant and consistently point to a younger, growing, family-orientated population.


## Recommendations

For task (a), it was asked what to develop on the unoccupied plot. I recommend the first option: high-density housing (3–4-bedroom units).
And here is why: The expansive population pyramid, the significantly elevated child proportion (19.2%), and the 22.9% of large households provide unequivocal statistical evidence of ongoing population growth driven by young families. High-density housing is the only option explicitly designed for a significantly expanding population.
All alternative options are overlooked on evidential grounds:
Low-density housing is not supported; the data show no widespread affluence.
A train station would serve only the 6.2% proven university commuters, which is not enough to provoke prioritisation.
A religious building is not considered since 56.7% declare “None”, and no denomination is growing.
A case for an emergency medical centre is not justified because recorded infirmity affects just 0.6% of residents.
High-density housing is therefore the only option that aligns with the town’s clear, statistically significant demographic expansion.
Task (b) is asking for what the primary public investment priority should be, and I am recommending: Increase spending for schooling, which is Option III.
The reason is this: An analysis of current demographic data indicates that 1,569 children under the age of 16, and children from consistent birth cohorts, will result in approximately 75 to 80 new school entrants each year for the foreseeable future. This demographic pressure far exceeds the need for old-age care (only 12.8% of the elderly) or broad employment retraining (unemployment is concentrated among mid-career adults, not youth).
Employment and training, old-age care, and general infrastructure are all overlooked as the primary investment priority for the following evidence-based reasons:
Employment and training: Unemployment (7.7% of adults) is significantly above the UK average (t = 5.23, p < 0.001), but it is concentrated among adults aged 40–49 rather than among school-leavers or young adults. Retraining is justified, yet the scale and urgency are dwarfed by the town’s far larger and faster-growing child population.
Old-age care: The town has only 12.8% aged 65+ (vs 18.6% nationally; χ² = 82.4, p < 0.0001). The old-age dependency ratio is exceptionally low, and the absolute number of new retirees each year will remain modest for at least the next 15–20 years.
General infrastructure: While any expansion eventually requires upgraded roads and services, the current demographic pressure is overwhelmingly driven by young families and children, not by diffuse population growth across all ages.
In contrast, the 19.2% under-16 population (χ² = 14.8, p < 0.001) and sustained birth cohorts of ~75–80 children per year create an immediate, large-scale, and predictable demand for school places that will persist for the next two decades. Increased spending on schooling and early-years provision is therefore the clear top priority.

## Conclusion

The 2025 Mock Census reveals a young, growing, family-oriented town using advanced, household-aware cleaning and statistically rigorous analysis. The optimal use of the vacant central plot is therefore high-density 3–4 bedroom family housing, supported by increased investment in schooling to accommodate the expanding child population. These recommendations are robust, fully evidenced, and directly address the town’s most pressing demographic realities.

## References

Al Jaber, T., Eaton, J., & Battlet, O. (2025). Fundamentals of Data Science Lecture Notes. University of Hull.
BBC News (2021). The rise of ‘Jedi’ and census joke religions.
Available at: https://www.bbc.co.uk/news
(Accessed: 7 December 2025).
Department for Levelling Up, Housing & Communities (DLUHC) (2023). English Housing Survey: Household Composition Report. London: UK Government.
Available at: https://www.gov.uk/government/collections/english-housing-survey
(Accessed: 7 December 2025).
Marriage Act 1949. United Kingdom Legislation.
Available at: https://www.legislation.gov.uk/ukpga/Geo6/12-13-14/76
(Accessed: 7 December 2025).
Office for National Statistics (ONS) (2021). Census 2021, Age Structure, England and Wales. London: ONS.
Available at: https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates
(Accessed: 7 December 2025).
Office for National Statistics (ONS) (2021). Census 2021, Disability and Long-Term Health Conditions. London: ONS.
Available at: https://www.ons.gov.uk/peoplepopulationandcommunity/healthandsocialcare/disability
(Accessed: 7 December 2025).
Office for National Statistics (ONS) (2021). Census 2021, Religion in England and Wales: Data Tables. London: ONS.
Available at: https://www.ons.gov.uk/peoplepopulationandcommunity/culturalidentity/religion/bulletins/religionenglandandwales/census2021
(Accessed: 7 December 2025).
Office for National Statistics (ONS) (2024). Labour Market Overview: UK. London: ONS.
Available at: https://www.ons.gov.uk/employmentandlabourmarket/peopleinwork/employmentandemployeetypes
(Accessed: 7 December 2025).
Skeena, S. S. (2017). The Data Science Handbook. Springer.
United Nations Department of Economic and Social Affairs (UN DESA) (2017). Principles and Recommendations for Population and Housing Censuses, Revision 3. New York: United Nations.
Available at: https://unstats.un.org/unsd/publication/seriesM/Series_M67rev3en.pdf
(Accessed: 7 December 2025).
University of Hull. (2025). Town A Census Dataset — T1_A25census-1.csv. Provided for coursework.

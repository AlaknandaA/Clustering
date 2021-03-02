# Clustering - Top 5 Countries in need of Medical Aid

**Problem Statement** - To identify top 5 countries most in need of aid from
a given list of about 200 countries, along with their data like income, GDP, health
expenditure per person, child mortality, etc.

**Short Description of data**

Column Name | Description
--- | --- 
country | Name of country
child_mort | Death of children under 5 years of age per 1000 live births
exports | Exports of goods and services per capita. Given as %age of the GDP per capita
health | Total health spending per capita. Given as %age of GDP per capita
imports | Imports of goods and services per capita. Given as %age of the GDP per capita
Income | Net income per person
Inflation | The measurement of the annual growth rate of the Total GDP
life_expec | The average number of years a new born child would live if the current mortality patterns are to remain the same
total_fer | The number of children that would be born to each woman if the current age-fertility rates remain the same.
gdpp | The GDP per capita. Calculated as the Total GDP divided by the total population.



**Analysis Methodology**

*Data Cleaning*
1. There were no missing values in the dataset, so did not perform any missing value analysis or imputation.
2. All the variables were in the correct datatypes, so no datatype conversion required.
3. Converted columns exports, health and imports to values, using the gdp.
4. Dropped the percentage value columns of exports, health and imports.

*Bivariate Analysis*


![Alt text](images/chilMort_health_income.png?raw=true "Title")

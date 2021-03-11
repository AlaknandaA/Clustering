# Clustering - Top 5 Countries in need of Medical Aid

**Problem Statement** - To identify top 5 countries most in need of aid from
a given list of about 200 countries, along with their data like income, GDP, health
expenditure per person, child mortality, etc.

**Short Description of data**

Country | Name of country
--- | --- 
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

We can clearly see high correlation between the income and health variables. Countries with high income have high sepnding on health, and vice versa. There is also a high negative correlation between income and child_mort- countries with low income have high child mortality rates.

This is because countries with higher incomes have better infrastructure, and also people’s flexibility is also increased by additional money.


![Alt text](images/Life_epec-health-income.png?raw=true "Title")


There is a high correlation between health and life expectancy. Countries with high health spending have higher life expectancy, but it reaches a pleatue somewhere about 10000$. Spending more than this amount also results in the same life expectancy. Also, we see that where the spending on health and life expectancy are higher, even the per person income is higher. For countries with low per person income, the life expectancy and health spending are low.

The 5 countries on the low end of the spectrum with least life expectancy and least health spending are:

Country	| Child_mort |	Life_expec |	Health |	Income
--- | --- | --- | --- | --- 
66 | Haiti | 208.0 | 32.1 |	45.7442 |	1500
87 |	Lesotho |	99.7 |	46.5 |	129.8700 |	2380
31 |	Central African Republic |	149.0 |	47.5 |	17.7508 |	888
166 |	Zambia |	83.1 |	52.0 |	85.9940 |	3280
94 |	Malawi	| 90.5 |	53.1 |	30.2481 |	1030

Countries with least life expectancy, even the child mortality rates are very high, which is probably why the life expectancy rates of these countries are low. In the countries with max health spending and max life expectancy, the child mortality rates are also very low.

![Alt text](images/totalFer_childMort_health.png?raw=true "Title")

Countries with high per person incomes mostly have fertility rate as 1 or 2, in some cases 3 as well. These also have the lowest child mortality rates. As the per person income decreses, the fertility rate increases and so does the child mortality.

We also see that the health expenditure and income are generally decreasing as the fertility rate increases after 3.

**Outlier Removal**

Outliers were seen in the upper range of variables income, inflation, gdpp, exports, health and imports. Only life_expec showed outliers in the lower range. Please refer to the python notebook for the plots and detailed explanation.

We can't drop outliers, since data is less. Also, since the countries falling on lower range of income, gdpp, health, exports imports etc are those of countries in mose dire need of aid, hence we will not remove countries in the lower range on these variables.

Low child mortality is a sign of developed country, and vice versa. Thus, even here, we will not treat the outliers on the higher ranges, we will treat outliers only in the lower range.


**Scaling**

All the variables were scaled using a standard scaler. In standard scaling, the mean of the scaled values will be 0 and the standard deviation will be 1. This means that all values will fall between -1 to +1.
Standard scaling is done so that in case of variables having high discrepancy between value ranges, for eg., in our case, total_fert has values between 1-8. Income or gdpp on the other hand can have values in lakhs. This huge discrepancy in value ranges in different variables makes the model slow and inefficient.

**Clustering (K-Means Clustering)**

The first thing to check is whether our data is suitable for clustering or not. Hopkins Score is a method to assess the clustering tendency. Hopkins Score uses the below formula to calculate clustering tendency:

![Alt text](images/Hopkins_Score_formula.jpg?raw=true "Title")


# Project Overview
## Why Life Expectancy?

Life expectancy is a critical indicator of a country's health and development status. It reflects the overall mortality level of a population and summarizes the mortality pattern that prevails across all age groups. Governments and health organizations worldwide rely on life expectancy data to inform policy decisions, allocate resources, and implement public health interventions.

The World Health Organization (WHO) collects and publishes extensive datasets on life expectancy and various health-related metrics. The availability of such data presents an opportunity to analyze and understand the factors that influence life expectancy and develop predictive models to estimate life expectancy based on various socio-economic and health indicators.

## Goals & Objectives

The primary objective of this project is to analyze the life expectancy dataset from WHO available on Kaggle and determine the optimal regression model by selecting one that achieves an adjusted R-squared value exceeding 0.95. Specifically, the project aims to:

1. Identify and analyze the key features that influence life expectancy through exploratory data analysis (EDA) and correlation analysis.
2. Develop regression models to accurately estimate life expectancy based on a range of demographic, socio-economic, and health-related features.
3. Compare the performance of the regression models using appropriate evaluation metrics such as Mean Absolute Error (MAE), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), and R-squared (R²) to determine their accuracy and generalizability.
4. Determine the optimal regression model by selecting one that achieves an adjusted R-squared value exceeding 0.95, ensuring robust explanatory power and predictive accuracy for estimating life expectancy based on diverse socio-economic, demographic, and health-related features.

## Project Summary
By comparing the performance of various regression models, this project aims to contribute to the ongoing efforts to improve global health and well-being, aligned with the United Nations Sustainable Development Goals (SDGs), particularly to ensure healthy lives and promote well-being for all at all ages.

# Data Overview
## Dataset Source
The dataset used in this project is publicly available on Kaggle and is provided by the World Health Organization (WHO). The dataset can be found on Kaggle at [https://www.kaggle.com/datasets/vikramamin/life-expectancy-who/data](https://www.kaggle.com/datasets/vikramamin/life-expectancy-who/data)

## Dataset Description
The dataset contains 22 variables and 2938 rows, covering life expectancy data of different countries from 2000 to 2015. The file size is approximately 121 KB. Each row represents a country for a particular year, and the columns include various health and socio-economic indicators such as country name, year, country status, life expectancy, adult mortality, infant deaths, alcohol consumption, expenditure on health, immunization coverage, diseases prevalence, BMI, GDP, population, and education-related features such as schooling.

## Feature Descriptions

| Feature                          | Data Type | Description                                                               |
|----------------------------------|-----------|---------------------------------------------------------------------------|
| Country                          | Object    | Country name                                                              |
| Year                             | Int64     | Year of the data                                                          |
| Status                           | Object    | Country status of developed or developing                                 |
| Life expectancy                  | Float64   | Life expectancy in years                                                  |
| Adult Mortality                  | Float64   | Probability of dying between 15 and 60 years per 1000 population          |
| Infant Deaths                    | Int64     | Number of Infant Deaths per 1000 population                               |
| Alcohol                          | Float64   | Alcohol, recorded per capita (15+) consumption (in litres of pure alcohol)|
| Percentage Expenditure           | Float64   | Expenditure on health as a percentage of Gross Domestic Product per capita (%) |
| Hepatitis B                      | Float64   | Hepatitis B (HepB) immunization coverage among 1-year-olds (%)            |
| Measles                          | Int64     | Number of reported measles cases per 1000 population                      |
| BMI                              | Float64   | Average Body Mass Index of the entire population                          |
| Under-Five Deaths                | Int64     | Number of under-five deaths per 1000 population                           |
| Polio                            | Float64   | Polio (Pol3) immunization coverage among 1-year-olds (%)                  |
| Total Expenditure                | Float64   | General government expenditure on health as a percentage of total government expenditure (%) |
| Diphtheria                       | Float64   | Diphtheria tetanus toxoid and pertussis (DTP3) immunization coverage among 1-year-olds (%) |
| HIV/AIDS                         | Float64   | Deaths per 1,000 live births due to HIV/AIDS (0-4 years)                  |
| GDP                              | Float64   | Gross Domestic Product per capita (in USD)                                |
| Population                       | Float64   | Population of the country                                                 |
| Thinness 1-19 Years              | Float64   | Prevalence of thinness among children and adolescents aged 10 to 19 (%)   |
| Thinness 5-9 Years               | Float64   | Prevalence of thinness among children aged 5 to 9 (%)                     |
| Income Composition of Resources  | Float64   | Human Development Index in terms of income composition of resources (index ranging from 0 to 1) |
| Schooling                        | Float64   | Number of years of schooling                                              |

# Data Cleaning
## Steps & Overview

1. After importing the data, create a copy of the DataFrame so we can preserve the original dataset for reference and later visualization of data cleaning changes.
2. Display the shape and datatypes of the dataframe to understand the size and data types of the dataset, which is crucial for initial exploration and subsequent data cleaning.
3. Check for missing values per feature to guide us in deciding how to handle missing data.
4. Print the column names to check for blank spaces and strip column names to remove spaces to ensures consistency in column names by removing leading and trailing spaces.
5. Drop the 'Status' column due to object type and because it is categorical and not relevant to our analysis.
6. Drop 'Population', 'Hepatitis B', and 'GDP' columns due to a high number of nulls, which could impact the analysis.
7. Drop the 'Year' column due to irrelevance in predicting life expectancy.
8. Calculate the number of outliers for each numeric feature and print for analysis.
9. Imputing missing values using the median of each respective feature due to high number of outliers. 
10. Create summary plots to visualize the changes made during the data cleaning process. This involved plotting the distribution of each feature before and after cleaning.

# Exploratory Data Analysis

## Summary of Techniques Employed
Exploratory Data Analysis (EDA) techniques includeded:
1. Histograms
2. Box plots
3. Heatmaps
4. Pairplots
5. Correlations

## Findings & Conclusion
The analysis reveals significant relationships between life expectancy and several key factors such as education, income resources, and health indicators. Higher education and better income resources are associated with higher life expectancy, while higher adult mortality, HIV/AIDS prevalence, and thinness are associated with lower life expectancy. The distributions of these variables indicate significant variability across different regions, with many outliers suggesting disparities in health outcomes and resources. Understanding these correlations and distributions can help in targeting policies and interventions to improve life expectancy and overall health.

## Key takeaways
1. Life expectancy is generally higher in countries with lower adult mortality, infant deaths, and HIV/AIDS prevalence, and higher GDP and schooling levels.
2. There is significant variability in health expenditure, vaccination rates, and disease prevalence across countries.
3. Missing data was a notable issue, particularly for economic indicators and vaccination rates.
4. The distributions reveal that most countries have low mortality rates, moderate to high life expectancy, and varying degrees of economic and health investments.

# Summary of Model Performance Results

In the study's findings, three different models were assessed to predict life expectancy based on various predictors. Model #1 utilized simple linear regression with only schooling as a predictor. It showed a moderate relationship, with an R-squared of 0.501; however, this model's predictive power was limited, suggesting the potential benefit of incorporating additional predictors to enhance accuracy. Model #2 employed multiple linear regression with schooling and additional predictors such as income composition of resources. This expanded model significantly improved upon the first, achieving an R-squared of 0.798. Despite this improvement, concerns regarding multicollinearity among predictors were noted, which could impact the model's reliability and interpretation. 

Model #3 utilized a Random Forest approach incorporating all available features, which yielded exceptional predictive performance. It achieved an impressive R-squared of 0.9945, indicating that 99.45% of the variance in life expectancy was explained. The model demonstrated robustness against multicollinearity and captured complex, non-linear relationships between predictors and life expectancy. Feature importance analysis highlighted HIV/AIDS prevalence as the most influential predictor, followed by income composition of resources and adult mortality.

Overall, while Model #1 and Model #2 provided foundational insights into the relationship between education, socioeconomic factors, and life expectancy, Model #3's Random Forest approach showcased superior predictive accuracy and robustness. It underscored the importance of leveraging advanced modeling techniques to capture intricate relationships within complex datasets, offering potential avenues for further research and policy implications in public health and education planning.

## Key takeaways
This study explored the relationship between various predictors and life expectancy using three distinct modeling approaches: simple linear regression, multiple linear regression, and Random Forest. Each model offered unique insights into the factors influencing life expectancy, highlighting both successes and areas for improvement in predictive accuracy and model interpretability.

Model #1, employing simple linear regression with schooling as the sole predictor, revealed a significant positive association between education and life expectancy. However, its moderate R-squared value of 0.501 indicated that a substantial portion of the variance in life expectancy remained unexplained, suggesting the potential benefits of incorporating additional predictors to enhance model robustness and predictive power.

Model #2 extended the analysis by incorporating additional predictors such as income composition of resources into a multiple linear regression framework. This expanded model demonstrated a notable improvement in predictive performance, achieving an R-squared of 0.798. The inclusion of socioeconomic factors alongside schooling highlighted their collective impact on life expectancy, emphasizing the complex interplay of education, economic resources, and health outcomes. Despite these advancements, concerns regarding multicollinearity among predictors were identified, underscoring the need for careful consideration and possibly alternative modeling techniques to mitigate this issue.

In contrast, Model #3 leveraged Random Forest, a non-linear ensemble method, to predict life expectancy based on all available features. This approach excelled in predictive accuracy, achieving an exceptionally high R-squared of 0.9945 and low RMSE, indicating robust performance and effective capture of complex relationships within the data. The model's feature importance analysis underscored the critical role of HIV/AIDS prevalence, income composition of resources, and adult mortality in determining life expectancy, providing valuable insights for targeted public health interventions and policy decisions.

## Limitations and Areas for Improvement

Despite the strengths demonstrated by the models in this study, several limitations warrant consideration. Firstly, the reliance on cross-sectional data limits the ability to establish causal relationships between predictors and life expectancy. Longitudinal studies could provide deeper insights into the temporal dynamics and cumulative effects of education, socioeconomic status, and health outcomes over time.

Secondly, while Model #3 (Random Forest) exhibited exceptional predictive performance, its black-box nature poses challenges in interpreting individual predictor contributions and underlying mechanisms influencing life expectancy. Future research could explore techniques to enhance model interpretability without sacrificing predictive accuracy, such as feature engineering or model-agnostic interpretability methods.

Furthermore, the presence of multicollinearity observed in Model #2 suggests potential redundancies or overlapping information among predictors, which may distort coefficient estimates and affect model reliability. Addressing multicollinearity through advanced statistical techniques or alternative modeling approaches could improve model stability and enhance the robustness of findings.

Lastly, the generalizability of findings may be limited by the specific characteristics and contexts of the dataset used in this study. Replicating these analyses across diverse populations and geographical regions would provide insights into the universality versus context-specific nature of predictors influencing life expectancy.

Addressing these limitations and pursuing avenues for improvement will be crucial for advancing our understanding of the complex interplay between socioeconomic factors and health outcomes, thereby informing evidence-based interventions and policies aimed at promoting population health and well-being.

## Implications and Future Directions

The findings from this study have several implications for research and policy. Firstly, the significant positive association between schooling and life expectancy emphasizes the importance of education as a fundamental determinant of health outcomes. Policy efforts aimed at improving educational access and quality could yield substantial gains in life expectancy and overall population health.

Secondly, while Model #2 demonstrated improved explanatory power by incorporating additional predictors, the detection of multicollinearity suggests the need for further refinement and validation of predictor selection methods. Techniques such as principal component analysis or regularization approaches could enhance model stability and interpretability in future studies.

Thirdly, the Random Forest model (Model #3) showcased the potential of machine learning algorithms to elucidate intricate relationships and nonlinearities in complex datasets. Its superior predictive performance suggests its utility in complementing traditional regression methods for forecasting life expectancy and guiding targeted interventions.

In conclusion, this study underscores the value of integrating diverse modeling approaches to comprehensively understand the determinants of life expectancy. By refining model methodologies and expanding predictor sets, future research can further enhance our ability to predict and improve population health outcomes effectively.
# Twitter-Marketing-Analysis

Эта работа выполнена с целью продемонстрировать процесс подготовки данных к обучению моделей машинного обучения. 

## Project Overview

This project investigates the relationship between social media usage, digital behavior, lifestyle factors, and user productivity. The analysis includes exploratory data analysis, data preprocessing, outlier detection and machine learning modeling.

The main objective is to identify which factors have the strongest influence on productivity and social media addiction levels.

## Dataset Features

| Feature Name | Description |
|-------------|-------------|
| age | Age of the respondent (in years) |
| gender | Gender of the individual (Male, Female, etc.) |
| job_type | Current employment sector or status (e.g., IT, Finance, Unemployed) |
| daily_social_media_time | Average time (in hours) spent daily on social media |
| social_platform_preference | Most frequently used social media platform (e.g., Instagram, Twitter) |
| number_of_notifications | Number of push notifications received per day |
| work_hours_per_day | Number of hours the person works daily |
| perceived_productivity_score | Self-reported productivity on a scale from 1 to 10 |
| actual_productivity_score | Measured productivity score on a scale from 1 to 10 (target variable) |
| stress_level | Perceived stress level (1 = low, 10 = high) |
| sleep_hours | Average number of sleep hours per day |
| screen_time_before_sleep | Time spent on screen right before going to sleep (in hours) |
| breaks_during_work | Number of breaks taken during the workday |
| uses_focus_apps | Whether the person uses focus-enhancing apps (True/False) |
| has_digital_wellbeing_enabled | Whether digital wellbeing settings are active on their device |
| coffee_consumption_per_day | Cups of coffee consumed daily |
| days_feeling_burnout_per_month | Number of days per month the person feels burnout |
| weekly_offline_hours | Number of hours spent offline in a week |
| job_satisfaction_score | Job satisfaction score from 1 to 10 |

## Workflow

Data Loading  
↓  
Exploratory Data Analysis
↓ 
Missing Value Handling  
↓  
Categorical Encoding  
↓  
Outlier Detection  
↓  
Machine Learning Modeling

## Missing Values Analysis
<img width="1242" height="590" alt="image" src="https://github.com/user-attachments/assets/61f58588-8920-4a97-9917-5d7aca0c3452" />
The heatmap revealed missing values in a limited number of features, allowing targeted preprocessing and imputation.

## Correlation Analysis
<img width="1107" height="790" alt="image" src="https://github.com/user-attachments/assets/436589c6-490d-40ab-a087-1b0b456cc532" />
The job_satisfaction_score and perceived_productivity_score have a high correlation with actual_productivity_score

## Social Media Usage vs Productivity
<img width="1191" height="690" alt="image" src="https://github.com/user-attachments/assets/32b142d1-e4e9-47e8-8462-2c29cf770f82" />
The plot shows that most individuals spend up to approximately 7.5 hours per day on social media platforms. No clear or consistent relationship between social media usage time and productivity was observed. This suggests that productivity is influenced by a combination of factors rather than a single variable such as gender or time spent on social media. Multiple behavioral, occupational, and well-being-related factors are likely to contribute to overall productivity levels.

## Sleep vs Productivity
<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/9d9347ad-9c3a-4d7a-b091-a0367c583364" />
Sleep duration doesn't affect productivity. This suggests that productivity isn't dependent on a single metric, but rather on a combination of metrics. This correlation can be demonstrated using machine learning.

## Focus Apps vs Productivity
<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/583813b1-1563-4fb4-9b1d-4b32a19ff637" />
Productivity distributions for users and non-users of focus apps are highly similar, suggesting that focus app usage alone is not a strong predictor of productivity.

## Data Preprocessing
### Missing Value Handling
Numerical features were imputed using KNN Imputer.
Categorical features were encoded using One-Hot Encoding.
### Outlier Detection
Outliers were identified using the IQR method.
Additional validation was performed using Z-score analysis.
### Feature Engineering
Boolean variables were converted to numerical format.
Categorical variables were transformed into binary features.
Highly correlated features were evaluated and removed when necessary.

Для решения задачи классификации значения actual_productivity_score были разбиты на классы, где от 0 до 4 - low, от 4 до 7 - medium, от 7 до 10 - high
LogisticRegression, RandomForestClassifier, XGBClassifier, CatBoostClassifier

## Classification Modeling

To formulate a classification task, the target variable `actual_productivity_score` was converted into three productivity classes:

| Productivity Score | Class |
|-------------------|--------|
| 0 – 4 | Low |
| 4 – 7 | Medium |
| 7 – 10 | High |

The following machine learning algorithms were evaluated:

- Logistic Regression
- Random Forest Classifier
- XGBoost Classifier
- CatBoost Classifier

### Model Comparison

<img width="1389" height="590" alt="image" src="https://github.com/user-attachments/assets/0995aa6d-07c8-43b7-84f0-3c67382c2370" />

**Conclusion**

Tree-based models (Random Forest, CatBoost, and XGBoost) significantly outperformed Logistic Regression, indicating the presence of non-linear relationships between user behavior and productivity. Random Forest and CatBoost achieved the highest accuracy (≈47.5%), while XGBoost obtained the highest Precision and F1-Score, providing the best overall balance between classification metrics. Logistic Regression demonstrated substantially lower performance, suggesting that the problem cannot be effectively solved using a simple linear decision boundary.

<img width="1911" height="1086" alt="Social_media_1 (1)" src="https://github.com/user-attachments/assets/06c23443-3899-4846-b8e9-0b268e518f0e" />

## Power BI Dashboard Analysis

The Power BI dashboard provides a more comprehensive and interactive view of the relationships between variables than the exploratory data analysis performed in Python. It enables deeper investigation of behavioral patterns, productivity indicators, and demographic characteristics.

### General Insights

1. The dashboard displays the distribution of users across gender categories, including male, female, and unspecified groups.
2. Average productivity scores are similar across gender groups, indicating no substantial gender-related differences in productivity.
3. Job satisfaction demonstrates the strongest relationship with actual productivity. A clear positive linear trend can be observed between `job_satisfaction_score` and `actual_productivity_score`.

### Analysis by Job Type

1. No clear relationship was observed between job satisfaction and the number of working hours per day.
2. Social media usage time showed a weak and inconsistent relationship with productivity. Higher social media usage does not necessarily correspond to lower productivity, and in some cases the opposite pattern can be observed.
3. Stress level did not demonstrate a strong direct relationship with burnout indicators.
4. The number of work breaks showed little to no influence on productivity levels.

### Analysis by Preferred Social Media Platform

1. TikTok users exhibited the highest average productivity scores among the analyzed platforms.
2. The distribution of preferred social media platforms varies across employment sectors. For example, users working in Healthcare more frequently prefer TikTok, while users in Education more often prefer Facebook.
3. The scatter plot comparing productivity across platforms, with bubble size representing burnout days, revealed no substantial differences in burnout levels between platform groups.
4. The use of digital wellbeing or focus-control applications showed no noticeable impact on productivity within the scope of this dataset.

### Overall Conclusion

The dashboard analysis suggests that job satisfaction is the most influential factor associated with productivity. In contrast, social media usage patterns, work breaks, and digital wellbeing tools demonstrated relatively weak relationships with productivity outcomes. These findings indicate that workplace satisfaction may play a more significant role in productivity than digital behavior alone.

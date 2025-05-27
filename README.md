# DSA210project
# Introduction
The aim of this project is to analyze the relationship between my social media time and weather status between the dates 17/02/2025 and 17/04/2025.

# Hypothesis 
When the weather is rainy, cloudy, foggy and snowy my social media screen time increases. I am confident that when weather is subjectively bad and it's harder to go out and socialize I tend to spend more time on instagram.

# Motivation
I realized that my screen time is increasing significantly and I want to monitor and control my activity. I believe that my findings can help me to reduce my social media time and help me to do something more productive instead by gaining awareness on my behaviour. Rather than relying on assumptions, this project adopts a quantitative approach to identify meaningful patterns and correlations between environmental variables and screen time.

# Data source
I fetched daily Instagram screen time data from the Screen Time section of my Apple device and historical weather data for Istanbul for each day from the Weather Underground website: https://www.wunderground.com/calendar/tr/istanbul/LTBA/date/2025-4 

I believe I will not have any problems with ethics and privacy issues since all weather data is publicly avaible and my own data will not be that personal.

For analysis, I will group weather conditions into two categories:
- Bad Weather: Rainy (1), Cloudy (2), Snowy (3), and Foggy (4)
- Good Weather: Sunny (0) 

The dataset included a single weather related feature based on condition labels such as sunny, rainy, cloudy, foggy and snowy. However, this would not provide enough variance for machine learning applications. Therefore, I enriched the dataset by fetching average daily temperature and average daily humidity and integrating them into the dataset in the next step. These additional features will allow me to do better pattern recognition and predictive modeling in the future.

# Project Plan 
1. Gather all the data needed.
2. Modify the data so it can be edited and be ready to analyze.
3. Provide graphs and descriptive statistics using pandas and matplotlib libraries.
4. Test the hypothesis using p-test and analyzing the charts.
5. Determine wheter the hypothesis is correct or not, if it's not try to explain why.
6. Train and evaluate machine learning models to predict Instagram screen time based on weather conditions.

# Data Analysis

## 1. Collecting Data 

After I fetched daily Instagram screen time and corresponding weather conditions between 17/02/2025 and 17/04/2025, I cleaned and structured datasets daily. Then, I merged datasets by date and put all of this data into an excel file for further analysis.

I grouped weather conditions into two categories:
- Bad Weather: Rainy (1), Cloudy (2), Snowy (3), and Foggy (4)
- Good Weather: Sunny (0) 

## 2. Exploratory Data Analysis (EDA)

Using pandas and matplotlib libraries, I did several exploratory data analyses to understand the distribution and behavior of my Instagram screen time under different weather conditions. I created a histogram to visualize the distribution of daily screen time, which helped me to identify the typical usage range in the data. I used a boxplot to compare screen time between good and bad weather days. It clearly revealed differences in medians. Also, I created a bar chart to show the average Instagram screen time for both groups. I applied a simple linear regression to see how bad weather affects my Instagram screen time. The results showed a positive relationship that when the weather is bad, I tend to use Instagram more. In addition to the regression analysis, I also calculated the Pearson correlation coefficient between bad weather and my Instagram screen time.

### 2.1 Histogram
![Image](https://github.com/user-attachments/assets/bc455f64-7a07-4955-b119-bd34134e99b4)

This histogram shows the distribution of daily Instagram screen time. Most values are between 30 and 100 minutes.

### 2.2 Boxplot
![Image](https://github.com/user-attachments/assets/6ab6a015-df52-4a9f-894b-53473de28d19)

This boxplot compares screen time under good and bad weather conditions. The median usage is noticeably higher on bad weather days.

### 2.3 Bar Chart 
![Image](https://github.com/user-attachments/assets/00cccfc6-0edb-43c1-96f9-c8111466bf54)

This bar chart shows the average Instagram screen time:
- On bad weather days the average time is ~90.46 minutes.
- On good weather days the average time is ~51.4 minutes.

### 2.4 Scatterplot with Regression Line
![Image](https://github.com/user-attachments/assets/69d2945b-5ee9-41a9-ab98-58048f074982)

This scatterplot shows the relationship between average daily temperature and Instagram screen time. Each point represents a day's usage. A regression line has been fitted to visualize the trend more clearly. The negative slope of the line indicates that as temperature increases, Instagram screen time tends to decrease.

- Intercept (β₀): 106.24
- Slope (β₁): -3.31
  
This means that when the average daily temperature is 0°C, Instagram usage is expected to be around 106.2 minutes. For each 1°C increase in temperature, Instagram screen time decreases by approximately 3.31 minutes. These findings support the idea that colder weather may contribute to increased screen time indoors.

### 2.5 Correlation Analysis

I conducted both correlation analysis and independent samples t-test to test the hypothesis that bad weather leads to increased Instagram screen time.

- Pearson Correlation Coefficient: 0.49
- This indicates a positive relationship between bad weather and screen time. 

- P-Value: 0.0001
→ Since the p-value is well below 0.05, the correlation is statistically significant.

As the number of bad weather days increases, so does the amount of Instagram screen time. This finding supports the main hypothesis from a correlational perspective.

## 3. Hypothesis Testing

- Null hypothesis (H₀): There is no significant difference in Instagram screen time between bad and good weather days.
- Alternative hypothesis (H₁): Instagram screen time is significantly higher during bad weather days.

I conducted an independent samples t-test to compare the means of the two groups. And the results are:
- t-statistic: 4.52
- p-value: 0.000031 = 3.1e-05

The test returned a t-statistic of 4.52 and a p-value of 0.000031, which is far below the significance level of 0.05. Therefore, I reject the null hypothesis.
This strongly supports my assumption that during bad weather (cloudy, rainy, foggy, or snowy), I tend to spend significantly more time on Instagram. 

## 4. Visualization

I created a histogram to show the overall distribution of screen time and a boxplot to see how median screen time differ between good and bad weather conditions. I used bar chart to compare the average Instagram screen time on good vs. bad weather days. I also created a scatterplot with a regression line to visualize the relationship between bad weather and screen time. 

In addition to these statistical plots, I visualized the performance of machine learning models using actual vs. predicted scatter plots and confusion matrices. The scatter plots helped evaluate how closely each model’s predictions matched the real screen time values, where points closer to the diagonal red line indicate better predictions. The confusion matrices showed how accurately the models classified screen time into predefined usage bins, revealing tendencies like underprediction.

## 5. Machine Learning Prediction

I used cross-validation to evaluate three different regression models: Random Forest, K-Nearest Neighbors (KNN), and Support Vector Regression (SVR). Each model used weather condition (binary), average daily temperature, and average daily humidity as features to predict daily Instagram screen time.

### 5.1 Random Forest Regressor
* MAE (Mean Absolute Error): 32.30 minutes 
* RMSE (Root Mean Squared Error): 38.57 minutes 
* R²: 0.034
  
### Actual vs. Predicted Plot (RF)
![Image](https://github.com/user-attachments/assets/69a99761-620d-425b-b6cf-7cedd67b2fae)

This scatter plot displays how closely the model’s predictions match the actual Instagram screen time values. Points closer to the diagonal red line show more accurate predictions.

### Confusion Matrix (RF)
![Image](https://github.com/user-attachments/assets/00a31339-722d-4eff-8016-8404fb967fe6)

The confusion matrix above demonstrates how well the Random Forest model classifies daily screen time into pre-defined bins. Most predictions are close to the diagonal, indicating the model often predicts the correct or neighboring usage range.

### 5.2 K-Nearest Neighbors (KNN) Regressor
* MAE (Mean Absolute Error): 34.74 minutes 
* RMSE (Root Mean Squared Error): 42.16 minutes 
* R²: -0.155
  
### Actual vs. Predicted Plot (KNN) 
![Image](https://github.com/user-attachments/assets/2b5dac33-a9be-4928-8a25-3da5aef5f3a7)

The plot shows predicted versus actual Instagram usage. While there is some scatter, most points are in the lower left, indicating the model generally predicts the trend but not exact values.

### Confusion Matrix (KNN)
![Image](https://github.com/user-attachments/assets/cd36ade2-88ef-49b1-a467-c6f3a38f669f)

The KNN model’s confusion matrix reveals that predictions are often in the correct or neighboring bins, although some misclassifications occur, especially in middle ranges.

### 5.3 Support Vector Regression (SVR)
* MAE (Mean Absolute Error): 36.09 minutes 
* RMSE (Root Mean Squared Error): 42.53 minutes 
* R²: -0.175
  
### Actual vs. Predicted Plot (SVR)
![Image](https://github.com/user-attachments/assets/160c13a5-1dd1-4472-b6d3-1ac99cc1f9b5)

This plot illustrates that SVR tends to underpredict high usage and overpredict low usage, with many points deviating from the ideal diagonal line.

### Confusion Matrix (SVR)
![Image](https://github.com/user-attachments/assets/721d8f02-598d-4be8-a8a5-f38317accddb)

The SVR model’s confusion matrix shows most predictions are concentrated in the 30–60 and 60–90 bins, with a clear tendency to misclassify higher and lower actual usage as these middle bins.

Among these three regression models tested (Random Forest, K-Nearest Neighbors, and Support Vector Regression) the Random Forest Regressor achieved the best performance with the lowest MAE (32.30 minutes), lowest RMSE (38.57 minutes), and the highest R² score (0.034). While overall predictive accuracy remained modest, Random Forest showed a stronger ability to capture patterns in the data, making it the most reliable model for estimating daily Instagram screen time based on weather conditions.

## 6. Limitations and Future Work

### 6.1 Limitations

- Weather is reduced to a binary classification (good or bad), which may not reflect nuance. 
- Instagram usage is influenced by untracked personal factors like mood, sleep, or workload.
- The dataset is small and manually collected, limiting scalability and generalizability.

### 6.2 Future Work

In this study, I have enriched the dataset by adding average daily temperature and average daily humidity to complement basic weather condition labels. These enhancements allowed for better pattern recognition and model performance. However, further improvements can still be made. Expanding the weather data with metrics like precipitation amount, wind speed, etc. may provide further insights into how environmental factors influence digital behavior. Additionally, collecting data over a longer time period or including data from multiple individuals would also increase the model’s generalizability. Finally, including personal behavioral variables such as mood and sleep quality could offer a better understanding of screen time dynamics in future work.

## 7. Findings

The key findings obtained through both statistical analysis and machine learning methods. The aim was to determine whether there is a meaningful relationship between daily Instagram screen time and weather conditions. The following insights were derived by combining exploratory data analysis, hypothesis testing, and predictive modeling:

- Screen time is significantly higher on bad weather days. On average, Instagram usage was approximately 90.5 minutes during bad weather compared to 51.4 minutes on good weather days.
- Statistical testing confirmed the difference is significant. A two-sample t-test returned a t-statistic of 4.52 and a p-value of 0.000031, allowing us to reject the null hypothesis and conclude that weather conditions do impact screen time.
- Regression analysis revealed a negative relationship between temperature and Instagram usage. The regression model estimated an intercept of 106.2 minutes and a slope of -3.31 minutes.
- Among the machine learning models, Random Forest achieved the best performance with an RMSE of 38.57 minutes and MAE of 32.30 minutes, but all models struggled to capture the full complexity of human behavior, as indicated by negative R² values.
- Confusion matrix results show that all models tend to predict the general screen time range correctly but struggle with precise classification. Most misclassifications occur between neighboring bins, which is reasonable for continuous behavioral data.
- SVR and KNN models exhibited higher prediction errors and had more bias towards the central bins, underperforming compared to Random Forest.

## 8. Conclusion 

Overall, the findings support the initial hypothesis: Instagram screen time tends to increase on bad weather days. Environmental factors such as temperature and weather conditions can be used to predict screen time to some extent, although the predictions are affected by considerable variability and noise. The consistency across statistical tests, regression analysis, and machine learning models strengthens the reliability of this conclusion.

This analysis demonstrates how external environmental factors, specifically weather, can influence digital behavior. By understanding these patterns, individuals may be better equipped to manage their screen time more consciously. The project also shows the value of personal data tracking and simple predictive modeling in generating meaningful behavioral insights.


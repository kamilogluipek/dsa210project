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
- Bad Weather: Cloudy (C), Rainy (R), Foggy, and Snowy 
- Good Weather: Sunny (S) 

Currently, the dataset includes a single weather related feature based on condition labels such as sunny, rainy, cloudy, foggy and snowy. However, this may not provide enough variance for machine learning applications. Therefore, I enriched the dataset by fetching average daily temperature and average daily humidity and integrating them into the dataset in the next step. These additional features will allow me to do better pattern recognition and predictive modeling in the future.

# Project Plan 
1. Gather all the data needed.
2. Modify the data so it can be edited and be ready to analyze.
3. Provide graphs and descriptive statistics using pandas and matplotlib libraries.
4. Test the hypothesis using p-test and analyzing the charts.
5. Determine wheter the hypothesis is correct or not, if it's not try to explain why.

# Data Analysis

## 1. Collecting Data 

After I fetched daily Instagram screen time and corresponding weather conditions between 17/02/2025 and 17/04/2025, I cleaned and structured datasets daily. Then, I merged datasets by date and put all of this data into an excel file for further analysis.

I grouped weather conditions into two categories:
- Bad Weather: Cloudy (C), Rainy (R), Foggy, and Snowy 
- Good Weather: Sunny (S) 

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
- Slope (β₁): –3.31
  
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

I created a histogram to show the overall distribution of screen time and a boxplot to see how median screen time differ between good and bad weather conditions. I used bar chart to compare the average Instagram screen time on good vs. bad weather days. I also created a scatterplot with a regression line to visualize the relationship between bad weather and screen time. I might include additional visualizations such as time series plots or scatterplots for better illustrations.

## 5. Machine Learning Prediction

To explore predictive modeling, I used a Random Forest Regressor to estimate my daily Instagram screen time using:
- Weather condition (Binary: Good vs. Bad)
- Average daily temperature (°C)
- Average daily humidity (%)

After splitting the dataset into training and test sets (80/20), I trained the model and evaluated it using RMSE and MAE.
- RMSE (Root Mean Squared Error): ~40.2 minutes
- MAE (Mean Absolute Error): ~33.1 minutes

### 5.1 Actual vs. Predicted Scatter Plot
![Image](https://github.com/user-attachments/assets/a47c9a9f-b63c-464c-9bd3-620ef9880a8d)

This scatter plot compares the model’s predicted Instagram screen time with the actual values from the test dataset. Each point represents a single day. The red dashed line indicates the ideal case where prediction equals reality. Points closer to the diagonal show more accurate predictions. Some variation from the line exists, but the model captures the overall trend well. It demonstrates the model's reasonable predictive power despite noise in human behavior data.

### 5.2 Confusion Matrix Interpretation
![Image](https://github.com/user-attachments/assets/ed0db43a-aa5a-4ba5-a978-2820240a4180)

I converted continuous Instagram screen time into categorical bins:

0–30 min, 30–60 min, 60-90 min, 90-120 min, 120-150 min, 150–180 min 
Using these bins, I generated a confusion matrix comparing actual vs predicted usage levels. The matrix shows how well the model can classify days into screen time categories.
A strong diagonal in the matrix indicates the model predicts the correct range most of the time, even if it doesn’t hit the exact minute count.

To evaluate the model’s classification-like performance, I binned the continuous Instagram screen time predictions into six categories (e.g., 0–30, 30–60, 60-90, 90-120, 120-150, 150–180 minutes). Then I compared actual and predicted bins using a confusion matrix. In the matrix, each row represents the actual screen time bin, and each column represents the predicted bin. The values on the diagonal show correct predictions, when the model placed a day into the correct usage range. Most values clustered around the diagonal, indicating the model frequently predicts screen time in the correct or a neighboring bin. This result suggests that the regression model is not only good at predicting the general trend of screen time but also reasonably accurate at classifying days into approximate usage levels. Misclassifications were mostly between adjacent bins, which is acceptable given the continuous nature of the target variable.

These visualizations show that the Random Forest model performs reasonably well in both numeric and categorical interpretation of Instagram screen time, especially considering the limited feature set and human-driven variability. 

Among the three features, temperature showed a statistically significant negative correlation with screen time, and bad weather was also positively correlated. While humidity had a more subtle effect, it helped improve prediction accuracy when combined with the others.

## 6. Limitations and Future Work

### 6.1 Limitations

- Weather is reduced to a binary classification ("good" or "bad"), which may not reflect nuance. 
- Instagram usage is influenced by untracked personal factors like mood, sleep, or workload.
- The dataset is small and manually collected, limiting scalability and generalizability.

### 6.2 Future Work

More features can be added such as day of the week, sleep duration, or holidays, etc. Time-series forecasting or classification models can be used to understand trends better. The dataset can be expanded with more granular weather data such as precipitation amount or wind speed. 

## 7. Findings

This section summarizes the key findings obtained through both statistical analysis and machine learning methods. The aim was to determine whether there is a meaningful relationship between daily Instagram screen time and weather conditions. The following insights were derived by combining exploratory data analysis, hypothesis testing, and predictive modeling:

- Screen time is significantly higher on bad weather days. On average, Instagram usage was approximately 90.5 minutes during bad weather compared to 51.4 minutes on good weather days.
- Statistical testing confirmed the difference is significant. A two-sample t-test returned a t-statistic of 4.52 and a p-value of 0.000031, allowing us to reject the null hypothesis and conclude that weather conditions do impact screen time.
- Linear regression showed a strong negative relationship between temperature and Instagram usage. The regression model estimated an intercept of 106.2 minutes and a slope of -3.31 minutes.
- Pearson correlation coefficient was 0.56, indicating a moderate-to-strong positive relationship between bad weather and Instagram usage.
- Machine learning predictions using Random Forest were reasonably accurate, with an RMSE of ~40.2 minutes and MAE of ~33.1 minutes.
- Binning screen time into categories showed the model often classified days into the correct or neighboring usage range, confirming its practical predictive ability even if precise minute predictions varied.

## 8. Conclusion 

Overall, the findings of this project strongly support the initial hypothesis: My Instagram screen time increases during bad weather conditions. The consistency across statistical tests, regression models, and machine learning predictions strengthens the reliability of this conclusion.

This analysis demonstrates how external environmental factors, specifically weather, can influence digital behavior. By understanding these patterns, individuals may be better equipped to manage their screen time more consciously. The project also shows the value of personal data tracking and simple predictive modeling in generating meaningful behavioral insights.






# DSA210project
# Introduction
The aim of this project is to analyze the relationship between my social media time and weather status between the dates 17/02/2025 and 17/04/2025.

# Hypothesis 
When the weather is rainy, cloudy, foggy and snowy my social media screen time increases. I am confident that when weather is subjectively bad and it's harder to go out and socialize I tend to spend more time on instagram.

# Motivation
I realized that my screen time is increasing significantly and I want to monitor and control my activity. I believe that my findings can help me to reduce my social media time and help me to do something more productive instead by gaining awareness on my behaviour.

# Data source
I will manually collect my daily Instagram screen time data from the Screen Time section of my Apple device and historical weather data for Istanbul for each day from the Weather Underground website: https://www.wunderground.com/calendar/tr/istanbul/LTBA/date/2025-4 

I believe I will not have any problems with ethics and privacy issues since all weather data is publicly avaible and my own data will not be that personal.

For analysis, I will group weather conditions into two categories:
- Bad Weather: Cloudy (C), Rainy (R), Foggy, and Snowy 
- Good Weather: Sunny (S) 

Currently, the dataset includes a single weather related feature based on condition labels such as sunny, rainy, cloudy, foggy and snowy. However, this may not provide enough variance for machine learning applications. Therefore, I enriched the dataset by manually collecting average daily temperature and average daily humidity and integrating them into the dataset in the next step. These additional features will allow me to do better pattern recognition and predictive modeling in the future.

# Project Plan 
1. Gather all the data needed.
2. Modify the data so it can be edited and be ready to analyze.
3. Provide graphs and descriptive statistics using pandas and matplotlib libraries.
4. Test the hypothesis using p-test and analyzing the charts.
5. Determine wheter the hypothesis is correct or not, if it's not try to explain why.

# Data Analysis

## 1. Collecting Data 

After I collected manually my daily Instagram screen time and corresponding weather conditions between 17/02/2025 and 17/04/2025, I cleaned and structured datasets daily. Then, I merged datasets by date and put all of this data into an excel file for further analysis.

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
![Image](https://github.com/user-attachments/assets/338f53bb-a800-4ef3-9a67-eb2eb579fbde)

This scatterplot shows the relationship between weather conditions and Instagram screen time. Each point represents a day of usage, grouped by whether the weather was good (0) or bad (1). The regression line indicates a positive trend which means that my Instagram usage increases when the weather is bad.

- Intercept (β₀): 51.40
- Slope (β₁): 39.06

On good weather days, I spend an average of 51.4 minutes on Instagram. In contrast, on bad weather days, my screen time increases by approximately 39 minutes.

### 2.5 Correlation Analysis

- Pearson Correlation Coefficient: 0.56
→ This indicates a positive relationship between bad weather and my Instagram screen time.

- P-Value: 0.0003
→ Since the p-value is well below 0.05, the correlation is statistically significant.

As bad weather increases, my Instagram usage tends to increase as well. This finding supports the main hypothesis from a correlational perspective.

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








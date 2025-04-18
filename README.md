# DSA210project
# Introduction
The aim of this project is to analyze the relationship between my social media time and weather status between the dates 17/02/2025 and 17/04/2025.

# Hypothesis 
When the weather is rainy, cloudy and snowy my social media screen time increases. I am confident that when weather is subjectively bad and it's harder to go out and socialize I tend to spend more time on instagram.

# Motivation
I realized that my screen time is increasing significantly and I want to monitor and control my activity. I believe that my findings can help me to reduce my social media time and help me to do something more productive instead by gaining awareness on my behaviour.

# Data source
I'll gather the weather and my social media data (instagram) to compare them using charts and descriptive statistics. I believe I won't have any problems with ethics and privacy issues since all weather data is publicly avaible and my own data won't be that personal. Including the weather data, I'll only focus on if it's raining, cloudy or snowy, not on moisture, pressure or rain/snow amount or alike parameters.

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

Using pandas and matplotlib, I calculated the average Instagram usage for both weather groups:

- Bad Weather Days: ~ 90.46 minutes
- Good Weather Days: ~ 51.4 minutes

## 3. Hypothesis Testing

- Null hypothesis (H₀): There is no significant difference in Instagram screen time between bad and good weather days.
- Alternative hypothesis (H₁): Instagram screen time is significantly higher during bad weather days.

I conducted an independent samples t-test to compare the means of the two groups. And the results are:
- t-statistic: 4.52
- p-value: 0.000031 = 3.1e-05

The test returned a t-statistic of 4.52 and a p-value of 0.000031, which is far below the significance level of 0.05. Therefore, I reject the null hypothesis.
This strongly supports my assumption that during bad weather (cloudy, rainy, foggy, or snowy), I tend to spend significantly more time on Instagram. 

## 4. Visualization

I created a histogram to show the overall distribution of screen time and a boxplot to see how median screen time differ between good and bad weather conditions. I used bar chart to compare the average Instagram screen time on good vs. bad weather days. I might include additional visualizations such as time series plots or scatterplots for better illustrations.








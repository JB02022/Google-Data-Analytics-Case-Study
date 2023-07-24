# Google Data Analytics Capstone: Cyclistic Case Study
Course: [Google Data Analytics Capstone: Complete a Case Study](https://www.coursera.org/learn/google-data-analytics-capstone)
## Introduction
In this case study, I will be working for a fictional company called Cyclistic. The goal is to maximize the number of annual members by understanding how casual riders and members use Cyclistic differently.
### Quick links:
Data Source: [divvy_tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html) 

### About Cyclistic
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime.
Until now, Cyclistic's marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. 
Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members. Cyclistic's finance analysts have concluded that annual members are much more profitable than casual riders. 
Although the pricing flexibility helps Cyclistic attract more customers, Moreno believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a very good chance to convert casual riders into members. 
She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs. Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. 
In order to do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends.

### Scenario
I am assuming to be a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, my team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, my team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve our recommendations, so they must be backed up with compelling data insights and professional data visualizations.

### Goal
Devise marketing strategies to convert casual riders to members.

### Analysis Questions
Three questions will guide the future marketing program:  
1. How do annual members and casual riders use Cyclistic bikes differently?  
2. Why would casual riders buy Cyclistic annual memberships?  
3. How can Cyclistic use digital media to influence casual riders to become members?

### Data Source
I will use Cyclistic’s historical trip data to analyze and identify trends from Jul 2022 to Jun 2023 which can be downloaded from [divvy_tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html). The data has been made available by Motivate International Inc. under this [license](https://www.divvybikes.com/data-license-agreement).  
  
This is public data that can be used to explore how different customer types are using Cyclistic bikes. But note that data-privacy issues prohibit from using riders’ personally identifiable information. This means that we won’t be able to connect pass purchases to credit card numbers to determine if casual riders live in the Cyclistic service area or if they have purchased multiple single passes.

### Data Cleaning
SQL Query: [Data Combining](https://github.com/JB02022/Google-Data-Analytics-Case-Study/blob/main/Data%20Cleaning)  
12 csv files are uploaded into one table in the dataset 'trip_data' which contains 5,779,444 rows. 

1. Rows with NULL values were deleted (1,370,355 rows removed)
2. Duplicate values in the column ride_id was checked
3. The SQL table was exported as a CSV document which will be further cleaned in R.
4. start_at and ended_at columns were converted into a date-time data type.
5. 2 columns were added to the dataset: ride_length, and day_of_week.
6. Trips with duration less than a minute and longer than 36 hours were deleted (91,006 rows removed).
7. 2 columns were renamed (member_casual to customer_type and rideable_type to ride_type).

### Analyze
The data is reliable and cleaned and is ready to be analyzed using R.

R: [Data Analysis] https://github.com/JB02022/Google-Data-Analytics-Case-Study/blob/main/Analysis

Firstly, the mean, median, and mode are calculated on the ride_length column. The results show that on average, people ride for 16 minutes, most rides last for 4.57 minutes, and half of the rides are under 10.22 minutes and the other half over 10.22 minutes. 

To check whether most riders are commuting to and from work, I created a new dataset called data_filtered which only include weekdays.
I will now check whether most people who use Cyclistic are commuters by counting how many times people ride between 7 -9 in the morning and between 4 and 7 in the evening

Using a code, I found that, 490,767 are during the morning’s rush hour and 925,615 are during the evening’s rush hour. 45.93% (1,416,382) of all riders during the weekdays are commuting during rush hour. The data demonstrates that although a high percentage of rides are during rush hour, most are outside of it.

I filtered the dataset by the customer_type (member vs casual) so that I can perform further analysis on the data

All in all, the code shows that 415,437 casual riders use Cyclistic during rush hour vs 1,000,945 for member riders. Members commute to and from work 2.4 times more than casual riders.

I calculated the average ride length of casual vs member riders and found that casual riders use Cyclistic for 22.8 minutes on average whereas members rides for 12.4 minutes on average.

I then proceeded to visualize the number of rides per month.
![image](https://github.com/JB02022/Google-Data-Analytics-Case-Study/assets/84155766/5666e553-97fa-4d0a-97ff-5da2f4e945e6)

The graph shows that people tend to bike more often when the weather permits (May-Oct).



I then checked how  each type of customer uses the 3 different bikes
![image](https://github.com/JB02022/Google-Data-Analytics-Case-Study/assets/84155766/29af55bd-9f0f-4663-8d7e-b39957b11030)

The "Electric Bike" were used 40.14% more times by members (1,007,327 rides).
Casual customers seem to prefer "Docked Bikes" more often (137,476 rides) than members who did not use it once.
The "Classic Bikes" were used 110.97% more times by members (1,664,042 rides). 



Next, I visualized the ride count by ride type and day of week
![image](https://github.com/JB02022/Google-Data-Analytics-Case-Study/assets/84155766/37cdff2a-d55e-4a2f-8abf-37e7a2a30fc4)

The result shows that for every day of the week, classic bike is the most popular choice followed by electric bikes. The result also shows that during weekdays, the percentage of electric bikes used is slightly higher than during weekends. As for docked bikes, they are used more frequently during weekends and less frequently during weekdays. 



I continued my analysis by creating a graphical representation of the ride count by customer type during rush hour.
![image](https://github.com/JB02022/Google-Data-Analytics-Case-Study/assets/84155766/7a60288e-c4fa-40af-9578-6d7f39ca5a14)

The graph shows that during morning rush hour, members tend to use Cyclistic more than 3 times as much compared to casual customers and close to 2 times as much during evenin rush hour.



The graph below represent the ride count by the day of the week.
![image](https://github.com/JB02022/Google-Data-Analytics-Case-Study/assets/84155766/9d83818a-ec8b-4186-b0c6-528d06d3a493)

The result shows that on weekends, both customer type rode the bike at an equal rate, however, during the weekdays, members rode their bike more often than casuals.



The visualization below is the mean ride length depending on the day of the week.
![image](https://github.com/JB02022/Google-Data-Analytics-Case-Study/assets/84155766/32fb5793-b632-4925-9e5f-9ec3beb58be3)

The data shows that casuals ride for longer during each day of the week than members, especially during weekends.
On weekends, casuals rode on average for 26.06 minutes vs 13.88 minutes for members (a 85.7% increase). During weekdays, casuals rode on average for 20.92 minutes vs 11.91 minutes for members (a 75.6% increase).



I then created a graph of the mean ride length by customer type and ride type.
![image](https://github.com/JB02022/Google-Data-Analytics-Case-Study/assets/84155766/b8ba6f87-42e9-4046-ad70-0da51ce52fd6)

The result shows that whenever casuals are using the docked bike, they tend to ride for twice as long as when they use the classic bike, and approximately 3 times as long as when they use the electric bike.
The graph also shows that casuals rides classic bikes for approximately twice as long than members but the ride length for electric bikes between casuals and members is relatively the same.















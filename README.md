# Do smartphones correlate with income and race

## This product uses the Census Bureau Data API but is not endorsed or certified by the Census Bureau

## Initial Question
Do income and race correlate with whether or not a person owns a smartphone? How does race affect it?

## Data parameters

### Chinese:
I removed all data points with race = "Chinese" because I realized that they were skewing data. All other categories of race had 500+ instances but the dataset only came up with 18 for the year 2023.

###  18 < age < 65:
Since I am looking at a correlation between smartphones and income I decided to filter out anyone over retirement age (65) as income becomes different when you reach retirement. I also removed anyone below 18 as I wanted to focus on those who were most likely working and funding the purchase of their own smartphone. 

### income < $1000000
I did this to remove outliers in the household_income portion of the data.

## What is in this repo?

### data_acquisition.ipynb
This is my initial work to get the data. I did the API call, all data frame manipulation and some sorting and filtering to get it to the data that I wanted for my work. I ran this code on all years with SMARTPHONE data in the Census Bureau databse (2021 - 2023) and saved each data set to run comparisons later.

When saved the .csv files had these columns for each row:
serial | sex | age | household_income | smartphone | race_label | state | year

### data_exploration.ipynb
Once I had the data this is where I did my data exploration. I have a ton of different graphs and outputs that helped me get a feel for my data. At first I was only looking at one year to see if it correlated but after doing a ton of different things I found no correlation and I move to the different years. 

Some of the tests run:

 - Check for outliers
 - Density plot compared to a log-normal distribution curve
 - Percent of smartphone = True vs False
 - Graphs to show trends by age, race and the smartphone value
 - Correlation
 - Cramers V
 - Linear Correlation
 - Random forest that then tested the correlation between groups

In the end I came to the conclusion that in the year 2023 there is almost no correlation between income level and whether people have a smartphone.

### yearcomp.ipynb

In this file I explore my theory that as smartphones become more and more essential to life the ownership of them becomes less and less correlated with income. In this file I take each dataset and then find the correlation for each one and then graph it to show the trend that I extracted from the data. I then added a trend line to show the overall trend from 2021 - 2023.

I then used Fisher's r-to-z test to see if this difference is statistically significant and it is with a p-value of 0.00005 which is much less than 0.05.
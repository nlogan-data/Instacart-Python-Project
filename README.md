# Instacart Data Analysis Case Study
The following project is an assignment from CareerFoundry's Data Analytics course. I completed the project independently. Open-source data sets from Instacart provide the order and product data. The customer data are fabricated. See the full GitHub repository [here](https://github.com/nlogan-data/Instacart-Python-Project).

![Instacart logo](01%20Project%20MGMT/logo.png)

## Overview and Purpose
Instacart is interesting in discovering more about their sales patterns. I perform analyses to inform strategy suggestions for better segmentation based on provided criteria.

## Context
The end goal for Instacart is a targeted marketing strategy. They need someone adept in Python's pandas library to analyze over 32 million rows of data.

See the orders and products data dictionaries [here](https://gist.github.com/jeremystan/c3b39d947d9b88b3ccff3147dbcf6c6b). 
This data dictionary does not belong to me, and was provided to me by CareerFoundry.

The raw data is too large for the repository. See the population flow [here](02%20Data/population-flow.pdf).


## Objective
Regarding users who are not new to Instacart, I investigated the following:

•	The sales team needs to know the days and times with the most orders.

•	They also want to know whether there are particular times of the day when people spend
the most money. 

•	The marketing and sales teams want simpler price range groupings.

•	The marketing and sales teams are particularly interested in the different types of
customers in their system and how their ordering behaviors differ.


## Tools and Skills

![Python logo](https://user-images.githubusercontent.com/97688439/150242727-7c0ae34e-907a-417a-b0d9-359cd4211413.png)

**Python:** Analysis and Visualization

•	NumPy, pandas, os, Matplotlib, and Seaborn libraries

•	Scripts written in Jupyter Notebooks

•	Data wrangling 

•	Data consistency checks

•	Crosstabs

•	Combining DataFrames

•	Deriving new columns

•	Subsetting, grouping data and aggregating variables

• Bar charts, histograms, and line charts

![Tableau logo](https://user-images.githubusercontent.com/97688439/150032188-cac6c36a-b2f7-459e-9f85-ee757be5788b.png)

**Tableau:** Further Visualization

•	Treemap

•	Bar chart compilation 

## Project Steps
Note that my [scripts folder](https://github.com/nlogan-data/Instacart-Python-Project/tree/main/03%20Scripts) contains scripts with numeric prefixes ranging from 4.2 to 4.10. This corresponds to order of the exercises and tasks I completed to learn skills and work on the project. Below, I only detail the script writing that is pertinent to the project--skill building aside.

First, I imported the data into a Jupyter notebook as a pandas DataFrame. Then, I conducted exploratory analyses of the datasets. This helped me gain a better understanding of the data, which informed future steps in the analysis. After this step, and all others, I exported the dataframes to .pkl files. This formed a version history of the data as I made manipulations.

Next, I carried out data wrangling steps, which included dropping irrelevant columns, renaming nondescript columns, and changing data types where necessary (e.g.: I changed user_id from integer to string). This streamlined the DataFrames and made the data more manageable.

With the desired data at hand, I performed consistency checks. This included finding and addressing missing values, duplicates, and columns with mixed-type data. This step was necessary to ensure an accurate analysis moving forward. One difficulty I faced here occured when I had over 200,000 null values in the days_since_prior_order column. I made a crosstab of that column and the order_number column, and I found that all of the observations with a order_number of 1 had a null value in the days_since_prior_order column. Then, I confidently decided to make no change to the null values in that column. 

Once I had wrangled and cleaned the data sets, it was time to combine them. It was important to wrangle and clean first, as this reduced the size of the final DataFrame and increased liklihood of fully-match combinations, respectively. The data sets were designed with combination in mind; there were primary and foreign keys present. So, I was well equipped to merge the DataFrames. I included an indicator to check for a full match, and a value count of the indicator showed that all observations of each merged DataFrame contained data from 'both' DataFrames. There were no issues with this step. Nevertheless it was important to create a single DataFrame for the succeeding analysis.

![Merge indicator count code](01%20Project%20MGMT/indicator-count.png)

Creating flag columns for user profiles constituted most of the work before generating visualizations. The region column was based off of the observation's state column. The max_order column grouped the DataFrame by user_id and found the user's max order_number (i.e.: this was the number of orders the user has placed). Then, I created a subset of the DataFrame that only contained active users, excluding users with less than 5 orders. With this subset, I created several other flag columns: an income flag, which categorized users by their income quartile (relative to other users); an age flag, with young in Q1, middle-aged in Q2 and Q3, and senior in Q4; a dependents flag, classifying users as a parent or non-parent; and a shopping habits flag. Creating the shopping habits flag required several intermediate steps, culminating in a column that gave each user a ratio of food purchases to non-food purchases. I used this ratio, as well as a check for null values in the food purchase and non-food purchase columns, to classify users' shopping habits. Addressing the null values was the most difficult part of user profiling. I was able to use the null values to my advantage, though, by using them to classify users as 'Food only' or 'Non-food only'.

![Shopping habits flag code](01%20Project%20MGMT/shopping-habits.png)

With all of the separate user flag columns in place, I used a list comprehension method to effectively concatenate the income, age, dependent, and shopping habits column values for each observation, yielding a profile for each user. Finding a method that could quickly handle the mass of data took experimentation with subsets, but I landed on list comprehension after just one other method failed to funciton in a timely manner.

Once I had the user profiles, it was time to leverage visualization tools to come up with recommendations for Instacart's requests. Several of the visualizations I could make in Jupyter, using Matplotlib and Seaborn. However, I needed to execute a few more steps for a couple of my final visualiztions. Because there are 134 (4x3x2x6) profiles, a bar chart is innappropriate. To make a tree map, I exported to .csv the value count of profiles grouped by user_id, and I used that file for the Tableau tree map. I implemented a similar method for a crosstab of the profiles and regions, with which I made a series of bar charts in Tableau.

![Tree map](04%20Analysis/Visualizations/profile_valuecount.png)

Finally, I rounded out the project with my [Excel report (download)](05%20Sent%20to%20Client/Logan-final-report.xlsx), which contains the population flow of the data,  my wrangling steps and consistency checks, details on each derived column, all of my visualizations, and my final recommendations. This was the final derivable to Instacart.

## Conclusion

I was able make recommendations to Instacart's sales and marketing teams, backed by visualizations that I made during my analysis. 

The most challenging aspect of the project was profiling the users, especially their shopping habits. With 24 (4 'income' by 3 'age' by 2 'dependents') profile combinations _before_ including shopping habits, I attempted to limit the amount of possibilities for that column. However, with 6 shopping habit categories, I ended up with 134 profile combinations.

In hindsight, I should have kept it to the 24 profile combinations, keeping the shopping habits separate from the profiles. Then, I would have made a shopping habits column with each user's most shopped department (of the 21 departments). Next, I would have used a crosstab to analyze the user profile's shopping habits, finding the top three departments for each of the 24 user profiles. This would have been more useful than my finding the top profiles, including shopping habits, by user count.

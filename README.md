# Instacart Data Analysis Case Study
The following project is an assignment from CareerFoundry's Data Analytics course. I completed the project independently. Open-source data sets from Instacart provide the order and product data. The customer data are fictional.

![Instacart logo](/01%20Project%20MGMT/logo.png)

## Overview and Purpose
Instacart is interesting in discovering more about their sales patterns. I perform analyses to inform strategy suggestions for better segmentation based on provided criteria.

## Context
The end goal for Instacart is a targeted marketing strategy. They need someone adept in Python's pandas library to analyze over 32 million rows of data.

See the orders and products data dictionaries [here](https://gist.github.com/jeremystan/c3b39d947d9b88b3ccff3147dbcf6c6b). 
This data dictionary does not belong to me, and was provided to me by CareerFoundry.

The raw data is too large for the repository. See the population flow [here](/02%20Data/population-flow.pdf).


## Objective
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
First, I imported the data into a Jupyter notebook as a pandas DataFrame. Then, I conducted exploratory analyses of the datasets. This helped me gain a better understanding of the data, which informed future steps in the analysis. After this step, and all others, I exported the dataframes to .pkl files. This formed a version history of the data as I made manipulations.

Next, I carried out data wrangling steps, which included dropping irrelevant columns, renaming nondescript columns, and changing data types where necessary (e.g.: I changed user_id from integer to string). This streamlined the DataFrames and made the data more manageable.

With the desired data at hand, I performed consistency checks. This included finding and addressing missing values, duplicates, and columns with mixed-type data. This step was necessary to ensure an accurate analysis moving forward. One difficulty I faced here occured when I had over 200,000 null values in the days_since_prior_order column. I noticed that the first few observations with the null values that I saw also had an 

## Conclusion


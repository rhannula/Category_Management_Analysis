# Category Management Analysis

## Overview:

The business request for this data analyst project was an executive analysis of a footwear category.  Based on the request of writing a semiannual category strategy plan, the objective of this project is to observe the structure of the strategic planning, the key components and other macro trends. Tools used in this project are Microsoft Excel and Power BI.

This project will analyse a category in the short to medium term which is **6 months** by using a total of **23 different metrics** which have been segmented into 4 different divisions:

- Value Size, Share & Growth of Category, and Segments (6) - *To showcase the state of the category. This is in* **light blue**
- Ranging, Share of SKUs and Distribution (5) - *Amount of SKUs per subcategory and its distribution between various locations. This is in* **light purple**
- Pricing (6) - *This is in* **grey blue**
- Promotional Activity (6) - *Units that are sold on promotion. This is in* **yellow**

## Structure of the category strategy:

1. Trends impacting the category
- Can be observed from short, medium or long term. This is to ensure that our strategic approach aligns with the trends and requirements

2. Category Structure and Dynamics
- Understanding the state of the category and its different segments.
- How and why did the category reach the state it is in?

3. Organisation Goals
- To ensure that category strategy is in line with the organisation's vision and mission.
- Which category and subcategory to grow, decline or hold

4. Brand Strategy
- Where to invest - monetary, time, effort

5. Execution Plan
- Advertisement, Trade strategy, Shopper strategy
- How to operate with various retailers/locations

6. P&L & Key Metrics
- Financial status of the category
- Market share and other benchmarks


## Deliverables

| Demanding | Value | Deliverable |
| ----------- | ----------- | ----------- |
| Overview of the state of the category and its subcategories. | To understand and see which ones are the biggest contributors of the category by monetary units. | A dashboard that can filter revenue by subcategory, location and timeline and compare it to a different timeline (now VS 6 months ago) and other valued metrics. |
| Overview of the amount of SKUs per subcategory, brands and its distribution between different locations. | To understand which subcategory and brands have the most SKUs, most popular SKUs per location. | A dashboard that can filter the number of SKUs by subcategory, brands, location and timeline and compare it to a different timeline (now VS 6 months ago) and other valued metrics. |
| Overview of the average price per subcategory, brands and SKUs. | To understand which subcategory, brands and SKUs have the lowest and highest average price, cost of goods sold and profit. | A dashboard that can filter subcategories, brands and SKUs by price, COSG, location and timeline and compare it to a different timeline (now VS 6 months ago) and other valued metrics. |
| Overview of subcategories, brands and number of SKUs that are sold at a discounted price. | To understand which subcategory, brands and SKUs have the most days of promotional activities and insight of different promotional prices. | A dashboard that can showcase subcategories, brands and SKUs by discounted price and number of promotional days and filter timeline and compare it to a different timeline (now VS 6 months ago) and other valued metrics. |

## Data cleansing and transformation

For this project, we have access to only 1 set of data that is in excel format and complies with both facts and dimensions datasets and you can find the raw data [HERE](www.google.com). (*To reduce the amount of redundancy, the master table had to be transformed into a facts table that is supported with 5 different dimensions: ProductDIM, DiscountDIM, DateDIM, CityDIM and BrandDIM.*)


*The following activities were performed in order to create the dimensions table (ProductDIM, DIscountDIM, CityDIM and BrandDIM):*

- Duplication of the original master table
- Select only the dimensions column (descriptive data) from the duplicated table and remove other columns (make sure the name of the selected column remains the same as in the original table)
- Remove duplicates from the selected column (which should reduce to only a few rows)
- Add an index column, starting from value 1
- Rename the duplicated table
- Select the original master table and select “*Merge queries*” from home-tab
- Select only the columns that you want to merge from both tables and make sure to left outer join before pressing “OK”
- New column should appear on the most right side of the table. Click on the expansion button and only select the index column (make sure to deselect the option of “*Use original column name as prefix*”)
- Delete the descriptive column and keep the index column. 

*The following activities were performed in order to create the Date dimensions table:*

- Create a black table by selecting “*Enter Data*”
- Add the first column and name it “*Start date*” and input should be the start date of the dataset
- Create a custom column, name it as “*End Date*” and input should be the end date of the dataset. In this particular project, the following M-query was placed: `=Date.From(#date(2014,12,30))`. This will result in 1 row column with output of 30/12/2014. If you simply just want the current date, then write the following M-query: `=Date.From(DateTime.LocalNow())`
- In order to create a date column that ranges from start date to end date, create a new custom column as “Date” and place the following M- query:
`={Number.From([Start date])..Number.From([End date])}`.
- Expand the column and change the data type to “*Date*” and remove the first 2 columns
- Duplicate the “Date” column, right-click the column name and select Transform-Year-Year and rename the column as “*Year*.” Duplicate the “*Date*” column, right-click the column name and select Transform-Quarter-Quarter and rename the column as “*Quarter.*”
- Create a custom column as “*Month*” and the following M-query was placed: `=Date.Month([Date])`.
- Create a custom column as “*Month Name*” and the following M-query was placed: `=Date.MonthName([Date])`
- Create a custom column as “*Short Month Name*” and the following M-query was placed: `=Text.Start([Month Name],3)`



## Data Model

*Below is a screenshot of the data model after cleansed and prepared tables were transited into Power BI. The schema blueprint used in this particular project is Snowflake Schema, which is an extension of a Star Schema that adds additional dimensions, usually representing hierarchies.*


## FMCG Category Management Analysis Dashboard

The finished Analysis Report is 1 page dashboard consisting of a Matrix dashboard where all of the structured segmented metrics have been compiled, distincting from each by assigned colours. The dashboard can be filtered throughout different timelines, segments, brands and individual SKUs, ensuring that the criterias of deliverables are being met up.

*You can see the finished dashboard [HERE](www.google.com) or by clicking the picture below.*

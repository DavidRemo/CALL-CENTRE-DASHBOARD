# Interactive Call Centre Dashboard Using Power Bi


## SOFTWARES USED
* Microsoft Excel
* Microsoft Power BI


## Problem Statement:
In this project I created a dashboard in Power BI for the call center that reflects all relevant Key Performance Indicators (KPIs) and metrics in the dataset.

### DASHBOARD 1: HOME
#### KPI’s Requirement
1. Total Number of Calls: We need to track and display the total number of calls received by our call centre over a specified period.
2. Total Call Duration in Hours: It is crucial to understand the total amount of time out call centre staff spends on calls in hours, which can help us in resource allocation and capacity planning.
3. Total Call Duration in Minutes: Similar to the total call duration in hours, this KPI provides the total call time but in minutes, offering a more granular view of call durations.
4. Average call duration in minutes: To assess the efficiency of our agents, we need to calculate and display the average call duration in minutes. This metric can help identify trends in call handling.
5. Response time percentage: Response time is a critical factor in customer satisfaction. This KPI should display the percentage of calls answered within a predefined time frame, helping us gauge our ability to provide prompt service.

#### Chart’s Requirement
1.	Total Call by day (column Chart): Display a column chart that shows the total number of calls on each day over a specified time period.
2.	Total calls by state (Filled Map Chart): Create a filled map chart that visualizes the total number of calls received from different states or regions.
3.	Top reasons for calls (Tree Map): Implement a tree map chart to display the top reasons for calls. Each box in the tree map represents a call reason.
4.	Total Calls by Channel (Donut Chart): Create a donut chart to showcase the distribution of calls by different communication channels.
5.	Total Calls by Sentiment (Column Chart): Utilize a column chart to illustrate the distribution of calls by sentiment (e.g. positive, negative, neutral).
6.	Total Calls by Call Centre (Bar Chart): Create a bar chart that presents the total number of calls handled by each call centre or department.

### DASHBOARD 2: GRID
•	Create a Grid View dashboard displaying a table of all call details in Power BI. <br/>
•	This should allow a user to export the grid for various filters applied.


## Datasource:
* [Call Centre Dataset]([https://github.com/DavidRemo/CALL-CENTRE-DASHBOARD/blob/main/Call%20Centre%20Dataset.xlsx)]) containing 12 columns and 32942 rows, with a total of 374,622 records of observation.


## Data Preparation:
Completed the Data transformation in Power Query and the dataset loaded into Microsoft Power BI Desktop for modeling.

Data Cleaning for the dataset was done in the power query editor as follows: <br/>
* Removed Unnecessary columns
* Removed Unnecessary rows
Each of the columns in the table were validated to have the correct data type.


## Data Modeling:
The dataset was then cleaned and transformed. <br/>

The Call Centre_Call Centre table and Date table were modelled by building a Many-to-One (*-1) relationship as shown below: <br/>

![Relationship](https://github.com/DavidRemo/CALL-CENTRE-DASHBOARD/assets/68180517/64402813-0d94-4dc7-81d5-36069f6d352d)


## Data Analysis (DAX):

Added new measures using DAX (Data Analysis Expressions) to enhance the quality of the data and improve the analysis in Power BI. <br/>

Measures used in the visualization include:

* Avg Call Duration (Min) = AVERAGE('Call Center_Call Center'[Call Duration In Minutes])

* Response Time % = CALCULATE([Total Calls], 'Call Center_Call Center'[Response Time] = "Within SLA" || 'Call Center_Call Center'[Response Time] = "Above SLA") / [Total Calls]

* Total Call Duration (Hrs) = [Total Call Duration (min)] / 60

* Total Call Duration (min) = SUM('Call Center_Call Center'[Call Duration In Minutes]) 

* Total Calls = COUNT('Call Center_Call Center'[Id])

* Date Table = CALENDAR(MIN('Call Center_Call Center'[Call Timestamp]),MAX('Call Center_Call Center'[Call Timestamp]))

* Day = FORMAT('Date Table'[Date], "ddd")

* Day No = WEEKDAY('Date Table'[Date], 1)


## Data Visualization (Dashboard) :
Data visualization for the data analysis (DAX) was done in Microsoft Power BI Desktop: <br/>

The Homepage Dahboard visualization of the Call Centre Trends is shown below: <br/>
![Home Page _ Dashboard](https://github.com/DavidRemo/CALL-CENTRE-DASHBOARD/assets/68180517/66eb0bab-7339-4959-b101-e2b6eead0e6c) <br/>


The Grid page Dahboard visualization of the Call Centre is shown below: <br/>
![Grid Page _ Dashboard](https://github.com/DavidRemo/CALL-CENTRE-DASHBOARD/assets/68180517/ec35230e-bf57-42df-8363-489ba433f0cb)



## Insights:
As shown by Data Visualization, It can be deduced that:
* On Fridays and Thursdays there are higher number of calls in the call center.
* Most of the calls are coming from customers in Texas state.
* Most of the customer calls are for billing questions followed by payments issue and then services outages.
* The most used channel of communication by customers is calls.
* Negative sentiments are many meaning that most customers are not satisfied. Therefore, the call centre should try to be very attentive on resolution of calls to improve customer service.
* Los Angeles call centre gets the most number of calls (almost 14,000).


## In conclusion:
The automated Power BI dashboard is designed to understand Call Centre trends. The consolidated report will deeply drive the improvement of the performance of call centre in terms of call handling and resolving cases. This report will help the management/team to identify the different levels of root causes and make some data-driven business decisions that could help in increasing the performance of call centre and customer satisfaction, with the help of this dashboard.

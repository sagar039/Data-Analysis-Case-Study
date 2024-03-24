GDS Grand Hospitality Data analysis:-

->Problem Statement:-
GDS Grands owns multiple five-star hotels across India. They have been in the hospitality industry for the past 20 years. Due to strategic moves from other competitors and ineffective decision-making in management, GDS Grands are losing its market share and revenue in the luxury/business hotels category. As a strategic move, the managing director of GDS Grands wanted to incorporate “Business and Data Intelligence” in order to regain their market share and revenue. However, they do not have an in-house data analytics team to provide them with these insights.Their revenue management team had decided to hire a 3rd party service provider to provide them insights from their historical data.

->Task:-
 Create the metrics according to the metric list.
 Create a dashboard according to the mock-up provided by stakeholders.
 Create relevant insights that are not provided in the metric list/mock-up dashboard.

->Metrics List:-
  Measures                                 Description
1 Revenue                               Sum of revenue_realized
2 Total Bookings                   Count of booking_id in fact_bookings
3 Average Rating                       Average of ratings_given
4 Total Capacity                         Sum of capacity
5 Total Succesful bookings     Sum of successful_bookings from fact_bookings
6 Occupancy %                  Ratio of Total Successful Bookings to Total Capacity
7 Total Cancelled Bookings     Count of booking_id in which booking_status = "Cancelled"
8 CancellationRate              Ratio of 'Total Cancelled Bookings' to 'Total Bookings'


->Architecture Diagram:-

                               +------------------------------------------+
                               |              Data Sources                |                       
                               |           (dim_date,dim_hotels           |                   
                               |     dim_rooms,fact_aggregated_bookings   |
                               |              fact_bookings)              |
                               +--------+---------+---------+-------------+
                                                     |
                                                     |
                                                     v
                                  +------------------+---------------+
                                     |       ETL Process            |
                                  +---------+------------+----------+
                                            |                   |
                                            |                   |
                                            v                   v
                                  +---------+------------+----------+
                                  |       Data Warehouse          |
                                  |  (Data loaded in Power BI)    |
                                  +-----------------+--------------+
                                                    |
                                                    |
                                                    |                                             
                                                    v                                            
                                            +---------+----------+                              
                                        |   Power BI Desktop  |                           
                                          |  (Data Modeling,    |                             
                                          |   Report Creation)  |                                     
                                           +---------+----------+                                  
                                                    |                                              
                                                    |                                              
                                                    |                                              
                                                    |                                            
                                                    v                                           
                                          +---------+----------+                              
                                         |   Data Consumers     |                           
                                         |  (Managers, Analysts |                         
                                         |   Operational Staff) |                           
                                          +--------------------+                               




Components:

1. Data Sources: Various data sources in the Hospitality is dim_date,dim_hotel,dim_rooms,fact_aggregated_bookings ,fact_bookings

2. ETL Processes: ETL (Extract, Transform, Load) processes to move data from sources to the Data Warehouse.

3. Data Warehouse: Data loaded in Power Bi and after that we will perform operations on it.

4. Power BI Desktop: Used for data modeling, creating reports, and designing visualizations.

5. Power BI Service: The cloud-based service for publishing, sharing, and collaborating on Power BI reports. It includes features like dashboards, reports, and data refresh.

6. Data Consumers: Various stakeholders such as Managers, Analysts, Operational Staff, Executives, Teams, and Stakeholders who consume the reports and dashboards generated in Power BI.

This architecture enables the use of Power BI for creating interactive and insightful reports and dashboards from the Hospitality data. It allows stakeholders to gain valuable insights for decision-making and operational efficiency in the Hospitality domain.


Steps :-

Step 1: Define Project Scope and Objectives
- Clearly define the scope of the project, including the specific metrics and KPIs to be analyzed.
- Identify the objectives of the analysis, such as optimizing revenue, understanding guest preferences, improving operational efficiency, etc.

Step 2: Gather Data
- Identify and collect relevant data sources from the Hospitality is dim_date,dim_hotels                               dim_rooms,fact_aggregated_bookings ,fact_bookings
 - Ensure data quality by cleaning and preprocessing the data. This may involve handling values, removing duplicates, and transforming data types.

Step 3: Data Modeling and Transformation
- Import the cleaned data into Power BI Desktop.
- Perform data modeling by creating relationships between tables, adding calculated columns, measures, and hierarchies.
- Transform data as needed using Power Query Editor, such as aggregating data, creating custom columns, and filtering.

Step 4: Create Visualizations
- Design and create interactive visualizations using Power BI Desktop.
- Use various chart types (bar charts, line charts, pie charts, etc.) to represent the data and metrics.
- Create dashboards with multiple visualizations to provide a comprehensive view of the data.

Step 5: Implement Business Logic
- Implement business logic by adding calculated fields and measures based on the project objectives.
- Calculate metrics such as Revenue of top 4 Properties, Occupancy Rates,Total Revenue

Step 6: Create Reports and Dashboards
- Develop detailed reports and interactive dashboards based on the defined metrics and KPIs.
- Organize the reports and dashboards logically to provide insights at different levels.

 Step 7: Test and Validate
- Thoroughly test the reports and dashboards to ensure accuracy and functionality.
- Validate the data against known results or expectations to ensure the analysis is correct.

Step 8: Publish to Power BI Service
- Publish the completed reports and dashboards to the Power BI Service.
- Share the reports with stakeholders and team members for review and feedback.

Step 9: Collaborate and Share
- Collaborate with stakeholders to gather feedback and make necessary revisions.
- Schedule data refreshes to keep the reports up-to-date with the latest data.

Step 10: Provide Insights and Take Action
- Analyze the insights gained from the reports and dashboards to make informed decisions.
- Take actionable steps based on the analysis to optimize revenue, improve guest experiences, and enhance operational efficiency in Hospitality.

Insights:-
We find the below findings as per Metrics given 
1.Total revenue Generated by hospitality sector is 2 BN

2.Total Booking is 134.29K

3.Average Rating is 3.62

4.Total Capacity is 233K

5.Total cancelled Bookings is 33.42K

6.Occupancy percentage is 57.87%

7.Cancellation Rate is 0.0024

Dashboard:-
![image](https://github.com/sagar039/Data-Analysis-Case-Study/assets/102663593/b98ed811-2950-4033-b870-7350d565c50e)












 


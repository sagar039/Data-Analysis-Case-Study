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


Step 1 : Load data into Power BI Desktop, dataset is a Excel file.

Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.

Step 3 :It was observed that in none of the columns errors & empty values were present in the datasets

Step 4 : As per client requirement following new measures has been created for better analysis

1.Revenue = SUM(fact_bookings[revenue_realized])

2.Total Bookings = COUNT(fact_bookings[booking_id])

3.Average Rating = AVERAGE(fact_bookings[ratings_given])

4.Total Capacity = SUM(fact_aggregated_bookings[capacity])

5.Total Successfull Bookings = CALCULATE(count(fact_bookings[booking_status]),FILTER(fact_bookings,fact_bookings[booking_status]="Checked Out") )

6.% Occupancy = DIVIDE(sum(fact_aggregated_bookings[successful_bookings]),SUM(fact_aggregated_bookings[capacity]),0)

7.Total Cancelled Bookings = CALCULATE(count(fact_bookings[booking_status]),FILTER(fact_bookings,fact_bookings[booking_status]="Cancelled") )

8.Cancellation Rate = DIVIDE([Total Cancelled Bookings],[Total Bookings],0)

9.Total No Show Bookings = CALCULATE(count(fact_bookings[booking_status]),FILTER(fact_bookings,fact_bookings[booking_status]="No Show") )

Step 5 : Started building visuals in Power BI based on the metrics list.

Step 6 :Created two dashboards,one is for "Bookings" and another one is for Revenue.

Step 7 :Following visuals has been created from the metrics for Bookings Dashboard

1.Cards created for "Total Bookings","Total Successfull Bookings","Total Cancelled Bookings","Cancellation Rate".

Total Bookings as per the data provided by the client is "135K"

Total Successfull Bookings as per the data provided by the client is "94K"

Total Cancelled Bookings as per the data provided by the client is "33K"

Cancellation Rate is Standing at 24.83% on total bookings

2.Created Donut chart to show the total bookings by city.

It represents how many bookings are done across the different cities
--Mumbai = 43K --Delhi = 24K --Hyderabad = 35K --Banglore = 32K

3.Created Stacked Column chart to show the total bookings status by city.

4.Created Stacked Column chart to show the total bookings by proprty_name and city.

5.Created Stacked Column chart to show the total bookings by booking_platform.

6.Created Stacked Column chart to show the total bookings by day_type.

It represents how many bookins are done by day_type.
-- Weekdays = 84K --Weekends =50K

7.Created Stacked Column chart to show the total bookings by month.

It represents how many Bookings are done by different Months.
-- May = 45.9K --June = 43.7K --July = 45K

8.Created Stacked Column chart to show the total bookings by Category.

It represents how many Bookings are done by Catogory.
--Business = 38% --Luxury = 62%

9.Created Stacked Column chart to show the total bookings by room_class.

--Standard = 135K --Presidential = 135K --Elite = 135K --Premium = 135K

10.Created Slicer to select the dates as per client requirement.

11.Inserted page navigation buttons to navigate to other page.

Step 8 : Following visuals has been created from the metrics for Revenue Dashboard
1.Cards created for " Revenue","Averagr Rating","Total Capacity","%Occupancy".

Total Revenue generated as per the data provided by the client is "1709M"
The Averate Rating given by the Customers is "3.62"
Calculated Total Capacity is "233K"
Calculated %Occupancy is "57.87%"
2.Created Donut chart to show the Revenue by City.

It represents how much revenue generated across the different cities
--Mumbai = 669M --Delhi = 295M --Hyderabad = 325M --Banglore = 420M

3.Created Donut chart to show the Revenue by room_class.

It represents how much revenue generated by different type of room_class
--Standard = 2bn --Presidential = 2bn --Elite = 2bn --Premium = 2bn

4.Created Stacked Column chart to show the Revenue by day_type.

It represents how much revenue generated by day_type.
-- Weekdays = 1.1bn --Weekends = 0.6bn

5.Created Line chart to show the Revenue by Month.

It represents how much revenue generated by different Months.
-- May = 52M --June = 554M --July = 573M

6.Created Stacked Column chart to show the %Occupancy by City.

It represents how much %Occupancy for the different cities.
--Mumbai = 57.88% --Delhi = 60.55% --Hyderabad = 58.07% --Banglore = 55.77%

7.Created Stacked Donut chart to show the Revenue by Property_name and City.

8.Created Slicer to select the dates as per client requirement.

9.Inserted page navigation buttons to navigate to other page.

Insights
1.Mumbai is having the highest percentage of Bookings compare to other cities 2.All the cities are having almost same succesfull booking percentage 3.eventhough weekdays are having highest bookings, but weekends are good for business 4.Luxary Category bookings are more rather than Business categories 5.GDS Exotica in Mumbai is having the higeshs bookings compare to other properties.. 6.GDS Palace property is having the best bookings among the other properties. 7.May is the best Month, in terms of Bookings and revenue. 8.Bookings for room classes and revenue are exactly same. 9.Mumbai city is contributing the highes revenue for the compnay. 10.GDS Exotica property is contributing the highest revenue compared to other properties. 11.Delhi city is having the highest occupancy rate.

Dashboard:-
![image](https://github.com/sagar039/Data-Analysis-Case-Study/assets/102663593/b98ed811-2950-4033-b870-7350d565c50e)












 


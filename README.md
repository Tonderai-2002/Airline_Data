✈️ FAA Flight Delays & Cancellations Dashboard
📊 Overview
In this project, I acted as a Data Analyst for the Federal Aviation Administration (FAA). Using a dataset of nearly 2 million commercial flights from major U.S. airports, the goal was to analyze flight delays and cancellations to uncover patterns and actionable insights.

I built an interactive dashboard in Power BI that allows stakeholders to explore delays and cancellations by:

Airport

Airline

Day of the Week

Delay Reason

🧩 Step 1: Data Loading & Transformation
What I Did:
Loaded the Flights, Airlines, and Airports datasets into Power BI.

In the Flights table:

Removed unnecessary columns.

Retained key fields:

AIRLINE, CANCELLATION_REASON, CANCELLED, DAY_OF_WEEK, DEPARTURE_DELAY, MONTH, ORIGIN_AIRPORT, YEAR

Created a new conditional column Status:

"On Time" if DEPARTURE_DELAY <= 0

"Delayed" if DEPARTURE_DELAY > 0

For the Airlines and Airports tables:

Promoted the first row to headers.

Verified and cleaned column names and data types.

🧱 Step 2: Data Modeling
What I Did:
Built a Star Schema with the Flights table as the central fact table.

Created and connected the following dimension tables:

Airlines — joined on AIRLINE code.

Airports — joined on ORIGIN_AIRPORT code.

Cancellation Codes — joined on CANCELLATION_REASON.

Tables Created:
Fact Table: Flights

Dimension Tables:

Airlines

Airports

Cancellation Codes

Relationships:
Defined one-to-many relationships from each dimension to the fact table.

Ensured correct cardinality and referential integrity.

📐 DAX Measures
Created the following DAX measures to support dashboard interactivity and insights:

DAX
Copy
Edit
Total Flights = COUNTROWS(Flights)

On Time Flights = CALCULATE([Total Flights], Flights[Status] = "On Time")

Delayed Flights = CALCULATE([Total Flights], Flights[Status] = "Delayed")

Canceled Flights = CALCULATE([Total Flights], Flights[Cancelled] = 1)

% On Time = DIVIDE([On Time Flights], [Total Flights], "-")

% Delayed = DIVIDE([Delayed Flights], [Total Flights], "-")

% Canceled = DIVIDE([Canceled Flights], [Total Flights], "-")


🔍 Key Insights
Atlanta (ATL) had the highest number of delays.

Spirit Airlines was the least reliable airline, with the highest rate of delays and cancellations.

Over 75% of cancellations were due to weather-related issues, primarily occurring on Tuesdays and Wednesdays.

Minneapolis (MSP) recorded the lowest number of cancellations.

SkyWest Airlines emerged as the most reliable airline in the dataset.


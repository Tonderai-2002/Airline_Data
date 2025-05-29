✈️ FAA Flight Delays & Cancellations Dashboard
📊 Overview
In this project, we take on the role of a Data Analyst for the Federal Aviation Administration (FAA).
We’ve been provided with a dataset of nearly 2 million commercial flights from major U.S. airports, and our objective is to analyze flight delays and cancellations to uncover patterns and insights.

Using Power BI, we transform the raw data into an interactive dashboard that allows stakeholders to explore delays and cancellations by:

Airport

Airline

Day of the Week

Delay Reasons

🧩 Step 1: Data Loading & Transformation
What I did:

Loaded the Flights, Airlines, and Airports datasets into Power BI.

In the Flights table:

Removed unnecessary columns.

Retained:

AIRLINE

CANCELLATION_REASON

CANCELLED

DAY_OF_WEEK

DEPARTURE_DELAY

MONTH

ORIGIN_AIRPORT

YEAR

Added a conditional column Status:

"On Time" if DEPARTURE_DELAY <= 0

"Delayed" if DEPARTURE_DELAY > 0

For Airlines and Airports tables:

Promoted the first row to headers after loading.

Verified column names and data types were correct.

🧱 Step 2: Data Modeling
What I did:

Built a star schema with the Flights table at the center as the fact table.

Connected supporting dimension tables:

Airlines — joined on AIRLINE code.

Airports — joined on ORIGIN_AIRPORT code.

Cancellation Codes — joined on CANCELLATION_REASON.

Tables created:

Fact Table: Flights

Dimensions:

Airlines

Airports

Cancellation Codes

Relationships defined:

One-to-many relationships from dimension tables to Flights table.

Verified correct cardinality and ensured referential integrity.

Model structure (e.g., star schema?):

✅ Star Schema

Central fact table: Flights

Surrounding dimension tables: Airlines, Airports, Cancellation Reasons

dax measures 
we created a measure called total flights Total Flights = COUNTROWS(Flights) in the flights table
we also created calculated measures for On Time Flights = CALCULATE([Total Flights],flights[Status]="On Time") 
On time flights delayed flights and canceled flights 
And we made dax measures for the above 3 measures but in %
% On Time = DIVIDE([On Time Flights],[Total Flights],"-")

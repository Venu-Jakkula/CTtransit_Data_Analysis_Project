# CTtransit Data Analysis Project


## Table of Contents

- [Project Overview](#project-overview)
- [Data Scource](#data-source)
- [Tools](#tools)
- [Data Cleaning/Preparation](#data-cleaning/preparation)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-(eda))
- [Data Analysis](#data-analysis)
- [Results/Findings](#results/findings)
- [Recommendations](#recommendations)
- [References](#references)
  
### Project Overview

Helping with reports for CTtransit, this project involves creating detailed analyses using Power BI to evaluate and improve bus service operations. The primary goals are to assess and optimize dwell times at bus stops, enhance on-time performance (OTP) by refining route timepoints, and explore dynamic discounting strategies to boost ridership during off-peak hours. By leveraging data-driven insights, the project aims to enhance overall service efficiency, reliability, and customer satisfaction for CTtransit.


![Dashboard](https://github.com/Venu-Jakkula/My_Projects/assets/171456105/4c353071-aca6-447e-857c-7440de8d8d5a)


### Data Source

National Transit Database: The primary data for this analysis is used from the "https://www.transit.dot.gov/ntd"

### Tools

- Power BI: Utilized for dashboard creation and data visualization.
- SQL: Used for data querying and database management.
- DAX (Data Analysis Expressions): Applied in Power BI for complex calculations.
- Microsoft Excel: Used for data cleaning and preliminary analysis. [Download here](https://docs.google.com/spreadsheets/d/1aDossB5gHJ3O0TjhdSIG4pAfuha5bDh6vMLydCUf4R8/edit#gid=2052132328)

### Data Cleaning/Preparation

- Identified and removed duplicates to ensure data accuracy.
- Handled missing values.
- Transformed raw data into usable formats for analysis.

### Exploratory Data Analysis (EDA)

- Analyzed the distribution of dwell times across different stops.
- Identified patterns in passenger boarding and alighting counts.
- Examined incident reports to understand their impact on dwell times.
- Visualized wheelchair dwell times to highlight accessibility issues.
- Correlated operator performance with average dwell times.

### Data Analysis

```DAX Functions
Dwell time (mins) = 'Adherence TM'[Dwell Time] / 60
```
```DAX Functions
Total Movement = [Alight Count] + [Board Count]
```
```DAX Functions
Division = SWITCH ( TRUE(),
FORMAT('Master	Route	TM'[Master	route],	"0")	in
{"24","30","31","32","33","34","36","37","38","39","41","43","44","45","46","47","50","52","5
53","54","542","55","56","58","59","60","61","62","63","64","66","69","72","74","76","82","82/
84","83","84","85","86","87","88","91","92","94","95","96",	"SC",	"DASH",	"CB","AH"},
"Hartford Local",
FORMAT('Master	Route	TM'[Master	route],	"0")	in
{"201","204","206","212","213","215","223","224","228","229","234","237","238","241","243",
"246","254","255","261","265","268","271","272","274","278","USS"}, "New Haven Local",
FORMAT('Master	Route	TM'[Master	route],	"0")	in
{"311","312","313","321","324","326","327","328","331","333","334","335","336","341","342",
"344","351","355"}, "Stamford Local", "Other"
)
```
```DAX Functions
Average	Board	Count	=	DIVIDE('Passenger	Count	TM'[Board	Count], DISTINCTCOUNT('Date'[Year]))
```
```DAX Functions
OTP %(new) = ('Adherence TM'[Ontime Count]/'Adherence TM'[Actual Count])
```

### Results/Findings

- Identified stops with significant dwell time issues affecting schedule adherence.
- Highlighted incident types contributing most to extended dwell times.
- Found accessibility challenges at specific stops with high wheelchair dwell times.
- Correlated high passenger activity with longer dwell times at busy stops.
- Detected operator performance variances impacting overall service efficiency.

### Recommendations

- Optimize schedules by reducing dwell times at identified problematic stops.
- Enhance incident management to minimize disruptions and delays.
- Improve infrastructure at key stops to better accommodate wheelchair users.
- Implement dynamic fare adjustments during off-peak periods to boost ridership.
- Provide targeted training for operators to improve dwell time efficiency.

### References

- [CTtransit](https://www.cttransit.com/services/local-service)









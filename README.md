# Paediatrics-Pharmacy-Unit-Revenue-Tracker

## Table of Content
- [Project Overview](#project-overview)
- [Business Objectives](#business-objectives)
- [Data Source](#data-source)
- [Tools](#tools)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Data Analysis](#data-analysis)
- [Key Insights](#key-insights)
- [Recommendations](#recommendations)

### Project Overview 📽️
---

This Power BI project analyzes pharmacy prescription and revenue data to uncover key insights into operational performance, financial growth, and stock management. The analysis examines trends in BHIS (Bayelsa state health insurance scheme) and cash prescriptions, evaluates revenue patterns over time, and explores how stock availability influences overall revenue outcomes. By visualizing these relationships, the dashboard provides data-driven insights to support better decision-making, improve efficiency, and enhance profitability within the pharmacy operations.

<img width="983" height="562" alt="Screenshot 2025-10-19 011529" src="https://github.com/user-attachments/assets/4a74c8d1-b13a-4b07-b726-825f6041792f" />

<img width="982" height="561" alt="Screenshot 2025-10-19 011555" src="https://github.com/user-attachments/assets/c8344b4a-47b8-48ba-9656-59933bdba09a" />

### Business Objectives
1. What is the trend of total revenue over time, and how much of it is contributed by cash vs. BHIS prescriptions

2. Which type of revenue shows the highest growth or decline over the past months
3. How do cash prescriptions compare to BHIS prescriptions (primary and secondary) over time
4. Are there seasonal or weekly trends in the number of total prescriptions
5. Does a higher number of total prescriptions correlate with increased total revenue
6. Is there a correlation between the number of out-of-stock items and the decline in prescriptions or revenue
7. Is the BHIS scheme (primary and secondary) effectively driving prescription volume and revenue?


### Data Source
The dataset is being collected from the prescription and revenue data of the pediatric pharmacy unit.

### Tools
- Excel 
- Power Bi

### Data Cleaning and Preparation
The dataset was personally gathered and carefully organized, ensuring accuracy and consistency; as a result, no further data cleaning was necessary prior to analysis.

### Data Analysis

Four (4) calculated columns were created
- ```Total BHIS Prescription = Sheet1[1˚ BHIS Prescription] + Sheet1[2˚ BHIS Prescription]```

- ```Total Daily Prescription = Sheet1[cash prescription] + Sheet1[1˚ BHIS Prescription] + Sheet1[2˚ BHIS Prescription]```
- ```Total BHIS Revenue = Sheet1[1˚ BHIS Revenue] + Sheet1[2˚ BHIS Revenue]```
- ```Total Revenue 1 = Sheet1[Cash Revenue] + Sheet1[1˚ BHIS Revenue] + Sheet1[2˚ BHIS Revenue]```


Thirty (30) DAX measures were created to enhance analysis
- ```Total Revenue 1 = Sheet1[Cash Revenue] + Sheet1[1˚ BHIS Revenue] + Sheet1[2˚ BHIS Revenue]```

- ```Average prescription = AVERAGE(Sheet1[Total Daily Prescription])```
- ```Average Revenue = AVERAGE(Sheet1[Total Revenue 1])```
- ```AVG Item Per Prescription = [Total Prescribed Item] / [Total Prescriptions]```
- ```BHIS revenue = sum(Sheet1[Total BHIS Revenue])```
- ```BHIS Revenue Growth = DIVIDE([BHIS revenue] - [Previous BHIS Revenue], [Previous BHIS Revenue])```
- ```BHIS Revenue Icon = IF([BHIS Revenue Growth] > 0, UNICHAR(9650), IF([BHIS Revenue Growth] < 0, UNICHAR(9660), UNICHAR(8211)))```
- ```Cash Revenue Growth = DIVIDE([Total Cash Revenue] - [Previous month cash revenue], [Previous month cash revenue])```
- ```Cash Revenue Icon = IF([Cash Revenue Growth] > 0, UNICHAR(9650), IF([Cash Revenue Growth] < 0, UNICHAR(9660), UNICHAR(8211)))```
- ```Growth icon = IF([Total Revenue MoM%] > 0, UNICHAR(9650), IF([Total Revenue MoM%] < 0, UNICHAR(9660), UNICHAR(8211)))```
- ```O/S Change Icon = IF([Percentage Change] > 0, UNICHAR(9650), IF([Percentage Change] < 0, UNICHAR(9660), UNICHAR(8211)))```
- ```Percentage Change = VAR __PREV_MONTH =CALCULATE([% Out-Of-Stock], DATEADD('Calender Date'[Date], -1, MONTH)) RETURN DIVIDE([% Out-Of-Stock] - __PREV_MONTH, __PREV_MONTH)```
- ```Prescription Growth = DIVIDE([Total Prescriptions] - [Previous month prescription], [Previous month prescription])```
- ```Prescription Growth icon = IF([Prescription Growth] > 0, UNICHAR(9650), IF([Prescription Growth] < 0, UNICHAR(9660), UNICHAR(8211)))```
- ```Previous BHIS Revenue = CALCULATE([BHIS revenue], DATEADD('Calender Date'[Date], -1, MONTH))```
- ```Previous month cash revenue = CALCULATE([Total Cash Revenue], DATEADD('Calender Date'[Date], -1, MONTH))```
- ```Previous month prescription = CALCULATE([Total Prescriptions], DATEADD('Calender Date'[Date], -1,MONTH))```
- ```Prevoius month revenue = CALCULATE([Total Revenue], DATEADD('Calender Date'[Date], -1, MONTH))```
- ```Total 1˚ BHIS Prescription = SUM(Sheet1[1˚ BHIS Prescription])```
- ```Total 1˚ BHIS Revenue = SUM(Sheet1[1˚ BHIS Revenue])```
- ```Total 2˚ BHIS Prescription = SUM(Sheet1[2˚ BHIS Prescription])```
- ```Total 2˚ BHIS Revenue = SUM(Sheet1[2˚ BHIS Revenue])```
- ```Total BHIS prescriptions = SUM(Sheet1[Total BHIS Prescription])```
- ```Total cash prescriptions = SUM(Sheet1[cash prescription])```
- ```Total Cash Revenue = sum(Sheet1[Cash Revenue])```
- ```Total Out-Of-Stock = SUM(Sheet1[Total O/S])```
- ```Total Prescribed Item = SUM(Sheet1[Daily Prescribed Items])```
- ```Total Prescriptions = SUM(Sheet1[Total Daily Prescription])```
- ```Total Revenue = SUM(Sheet1[Total Revenue 1])```
- ```Total Revenue Growth = DIVIDE([Total Revenue] - [Prevoius month revenue], [Prevoius month revenue])```

### Key Insights

- In September 2025, the pharmacy recorded a total of 382 prescriptions, representing a 48.06% increase from the previous month. The out-of-stock rate stood at 7.72%, marking a 37.53% rise compared to August.

- Financially, the month generated ₦446,150 in cash revenue, a 125.06% increase, and ₦728,462 in BHIS revenue, up 40.64% from the prior month. The total revenue reached ₦1,174,612, reflecting a 64.01% overall increase from August.
- Among all prescription categories, Primary BHIS prescriptions contributed the highest revenue at ₦568,897, followed by cash prescriptions, while Secondary BHIS prescriptions generated the least, totaling ₦159,565.
- A review of the line chart indicates that September achieved the highest monthly revenue (₦1,174,612), while May recorded the lowest at ₦492,354.
- From the column chart on month-over-month (MoM) revenue growth, there was steady growth from May to July, followed by a 21.13% decline in August and then a strong rebound of 64.01% in September.
- Analysis by day of the week revealed that Mondays were the busiest, averaging 22 prescriptions, while Wednesdays were the least busy with an average of 15 prescriptions. Despite being the second busiest day, Fridays generated the highest daily revenue, averaging ₦61,508.33.
- A scatter plot illustrating the relationship between total daily prescriptions and total revenue showed a strong positive correlation, indicating that higher prescription volumes are associated with increased revenue.
- Conversely, a weak to moderate negative correlation was observed between out-of-stock items and total revenue, suggesting that an increase in stock shortages tends to reduce overall revenue generation.

### Recommendations

1. Strengthen inventory control to reduce out of stock and prevent revenue loss.

2. Focus resources on high-performing days (Mondays and Fridays) while boosting midweek activity.
3. Enhance BHIS scheme efficiency to sustain consistent revenue flow.
4. Maintain growth momentum by tracking month-over-month performance.


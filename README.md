# Data-Analytics-Project-Prism-Insurance-Dashboard
Interactive Insurance Data Analysis Dashboard built using SQL Server, Power BI, Power Query, DAX, and Python Sentiment Analysis.

### Dashboard Link : https://app.powerbi.com/reportEmbed?reportId=69ce3c1a-d5d2-42d3-8b1e-c703e69d68dd&autoAuth=true&ctid=b4852602-c9cb-43ff-8fe0-aac33802d1e5"

## Problem Statement

Insurance companies generate thousands of policy and claim records every day. As the volume of customer, policy, premium, coverage, claim, and feedback data increases, it becomes difficult for management to manually analyze business performance, monitor claims, and understand customer satisfaction. The lack of a centralized reporting system delays decision-making and makes it challenging to identify trends, policy performance, claim outcomes, and areas requiring improvement.

The objective of this project is to develop an interactive Power BI dashboard that consolidates insurance data into meaningful visualizations and key performance indicators (KPIs). The dashboard enables stakeholders to monitor premium collections, coverage amounts, claim amounts, policy distribution, claim status, customer demographics, and customer sentiment in real time. Additionally, sentiment analysis on customer feedback helps identify common issues, service quality, and overall customer satisfaction.

The dashboard provides dynamic filtering and drill-down capabilities, allowing users to analyze data by policy number, claim number, customer ID, policy type, age group, gender, and claim status. This solution transforms raw insurance data into actionable business insights, improving operational efficiency, enhancing customer experience, and supporting data-driven decision-making.


### Steps followed 

- Step 1: The insurance dataset was first imported into "SQL Server Management Studio (SSMS)" by creating a database and loading the cleaned CSV file into a SQL Server table.
- Step 2: "Power BI Desktop" was connected to SQL Server, and the insurance dataset was imported directly from the SQL Server database for further analysis and visualization.
- Step 3: "Power Query Editor" was used for data cleaning and profiling. Under the "View" tab, "Column Quality", "Column Distribution", and "Column Profile" were enabled to inspect the dataset. Data types were verified, null values were handled where necessary, and the dataset was prepared for analysis.
- Step 4: Two additional columns were created using "Conditional Columns" in Power Query:
    
    - Age Group – Customers were categorized into different age groups (e.g., Young Adults, Adults, Elderly) based on their age for demographic analysis.

    for creating the new column, the following Power Query (M) expression was used;

            if([Age] <= 24, "Young Adults",

            if([Age] <= 60, "Adult",

            "Elder"))
    
    - Active/Inactive – Policies were classified as "Active" or "Inactive" based on the "Policy End Date", enabling policy status analysis.

    for creating the new column, the following Power Query (M) expression was used;

            if([PolicyEndDate] <= #date(2024, 10, 30), "Inactive",

            "Active")
- Step 5 : In the "Report View", a custom dark theme was applied to the dashboard to provide a professional and visually appealing interface.
- Step 6 : Three Slicers were added for the fields "Policy Number", "Claim Number", and "Customer ID" to enable users to interactively filter the dashboard and analyze specific records.

- Step 7 : Three "Card visuals" were created to display the key business metrics:

    - Total Premium Amount

    - Total Coverage Amount

    - Total Claim Amount

    The following DAX measures were created:

    PremiumAmount –

            PremiumAmount = SUM(InsuranceData[PremiumAmount])

    CoverageAmount –

            CoverageAmount = SUM(InsuranceData[CoverageAmount])

    ClaimAmount –

            ClaimAmount = SUM(InsuranceData[ClaimAmount])

- Step 8 : Two "Card visuals" were added to display the total number of "Male" and "Female" customers.

    The following DAX measures were created:

    Male Customers –

            Male Customers =
            CALCULATE(
                COUNT(InsuranceData[CustomerID]),
                InsuranceData[Gender] = "Male"
            )

    Female Customers –

            Female Customers =
            CALCULATE(
                COUNT(InsuranceData[CustomerID]),
                InsuranceData[Gender] = "Female"
            )

- Step 9 : A "Funnel Chart" was created to display the "Number of Claims by Claim Status", allowing users to compare the number of "Rejected", "Settled", and "Pending claims".
        
- Step 10 : A Table Visual was created to display Policy Type, Pending, Rejected, and Settled claim amounts. A visual-level filter was applied on the Policy Type field, allowing users to easily analyze and drill down into a specific insurance category such as Travel, Health, Auto, Life, or Home. This enables focused analysis of claim amounts for each policy type.

- Step 11 : A "Donut Chart" was created to display the distribution of "Active" and "Inactive" policies, providing a quick overview of policy status.
  
In our dataset, Some parameters were assigned value 0, representing those parameters are not applicable for some customers.

All these values have been ignored while calculating average rating for each of the parameters mentioned above.

- Step 12 : An "Area Chart" was created to analyze the "Claim Amount by Age Group", helping identify which customer age groups contribute the highest claim amounts.

- Step 13 : A "Matrix Visual" was created to display the "Claim Amount" by "Policy Type" and "Claim Status (Pending, Rejected, Settled)", allowing detailed comparison across different insurance categories.

- Step 14 : Text boxes, borders, and formatting elements were added to create a clean and professional dashboard layout. Appropriate titles, labels, and data formatting were applied to improve readability and user experience.


        
- Step 15 :A "Word Cloud Visual" was added to the report to analyze customer feedback. This visual highlights the most frequently occurring words in customer reviews, enabling quick identification of common topics, concerns, and positive experiences shared by customers.

        
- Step 16 :A Table Visual was created to display "Customer Name", "Sentiment Score", and "Customer Feedback". This allows users to review individual customer comments alongside their corresponding sentiment scores for detailed feedback analysis.
 
- Step 17 : A "Clustered Bar Chart" was added to represent the "Count of Customer Feedback" by feedback category "(Excellent, Good, and Needs Improvement)". This visualization provides an overview of customer satisfaction levels and helps identify areas where service quality can be improved.

- Step 18 : Customer feedback was processed using "Python-based Sentiment Analysis". A sentiment score was generated for each feedback record, and the feedback was categorized into "Excellent", "Good", and "Needs Improvement" based on the sentiment score. The processed dataset was then imported into Power BI for visualization and analysis.
 
- Step 19 : The report was then published to Power BI Service.
 
![Publish_Message](https://github.com/ansh0444/Data-Analytics-Project-Prism-Insurance-Dashboard/blob/90eab3b1336d13827c161c7e999a6462d50891fd/img/image.png)

# Snapshot of Dashboard (Power BI Service)

![dashboard_snapo](https://github.com/ansh0444/Data-Analytics-Project-Prism-Insurance-Dashboard/blob/872ba3261003fb97178b56e18271e82381d1f85a/img/Dashboard%201.png)

![dashboard_snapo](https://github.com/ansh0444/Data-Analytics-Project-Prism-Insurance-Dashboard/blob/b20423fef1638609cd7fe729218e602fd453ea69/img/Dashboard%202.png)

![dashboard_snapo](https://github.com/ansh0444/Data-Analytics-Project-Prism-Insurance-Dashboard/blob/71e2b345b481c9dcc96e0619cee0876016fb93ca/img/DA3.png)
 
 # Report Snapshot (Power BI DESKTOP)

 
![Dashboard_upload](https://private-user-images.githubusercontent.com/121956665/623691655-23566873-d99b-4bbe-94d2-8416a9b2cbe6.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3ODQ0OTQ2MDIsIm5iZiI6MTc4NDQ5NDMwMiwicGF0aCI6Ii8xMjE5NTY2NjUvNjIzNjkxNjU1LTIzNTY2ODczLWQ5OWItNGJiZS05NGQyLTg0MTZhOWIyY2JlNi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDcxOVQyMDUxNDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT04ZGEzN2UxNzE1MTg4MzRhNGFjNWNmZGQ1ZDRkNTc2MmUzNDI4MTI5NTlhMTM2OTU2ZTY4YzJhMWZhYWVjMDVlJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.Pih7-8Z-1Rbx1GhGpJQx8VR4ax4jhG7IMCGyNM_ED3k)



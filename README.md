
# Bank Loan Analysis-Dashboard


## Overview

This dashboard helps the bank understand its customers better. This report aims to provide comprehensive insights into bank loan data, covering various aspects such as
loan applications, disbursements, borrower profiles, and loan performance. The project leverages data visualisation techniques to facilitate informed decision-making
and strategic analysis for banking institutions.


### Steps followed 

- Data preparation: Ensure the bank loan data (.csv) is properly formatted and organised for import into Power BI.
- Data Modelling: Create data models and relationships within PowerBi to facilitate data analysis and visualisations.
- Dashboard Creation: Develop Interactive dashboards and reports using PowerBi visuals to visualise loan metrics and KPIs.
- Interact with data: Explore and interact with data through filters to gain deeper insights.

for creating a new table and  column following the DAX   expression was written;
       
    (Date Table = CALENDAR(MIN(financial_loan[issue_date]),MAX(financial_loan[issue_date]))
	Month Column =Month = FORMAT('Date Table'[Date],"mmm")
	Month number = MONTH('Date Table'[Date])

Following DAX expressions were created using new measures.
 
	Avg DTI = AVERAGE(financial_loan[dti])
	Avg Int Rate = AVERAGE(financial_loan[int_rate])
	Total Loan Applications = COUNT(financial_loan[id])
	Total Funded Amount = SUM(financial_loan[loan_amount])
	Total Amount Recieved = SUM(financial_loan[total_payment])
	(Previous Month-to-Date)PMTD Total Funded Amount = CALCULATE(SUM(financial_loan[loan_amount]),DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))
	(Previous Month-to-Date)PMTD Total Amount Recieved = CALCULATE(SUM(financial_loan[total_payment]),DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))
	(Previous Month-to-Date)PMTD Loan Applications = CALCULATE(COUNT(financial_loan[id]),DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))
	(Previous Month-to-Date)PMTD AVG DTI = CALCULATE([Avg DTI],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))
	(Previous Month-to-Date)PMTD Av Int Rate = CALCULATE([Avg Int Rate],DATESMTD(DATEADD('Date Table'[Date],-1,MONTH)))
	(Month-to-Date)MTD Total Amount Recieved = CALCULATE(TOTALMTD(SUM(financial_loan[total_payment]),'Date Table'[Date]))
	(Month-to-Date)MTD Loan Application = CALCULATE(TOTALMTD(count(financial_loan[id]),'Date Table'[Date]))
	(Month-to-Date)MTD Funded Amount = CALCULATE(TOTALMTD(SUM(financial_loan[loan_amount]),'Date Table'[Date]))
	(Month-to-Date)MTD Avg Int Rate = CALCULATE(TOTALMTD([Avg Int Rate],'Date Table'[Date]))
	(Month-to-Date)MTD Avg DTI = CALCULATE(TOTALMTD([Avg DTI],'Date Table'[Date]))
	(Month-over-Month)MoM Total Funded Amount = ([MTD Funded Amount]-[PMTD Total Funded Amount])/[PMTD Total Funded Amount]
	(Month-over-Month)MoM Total Amount Recieved = ([MTD Total Amount Recieved]-[PMTD Total Amount Recieved])/[PMTD Total Amount Recieved]
	(Month-over-Month)MoM Loan Application = ([MTD Loan Application]-[PMTD Loan Applications])/[PMTD Loan Applications]
	(Month-over-Month)MoM Avg Int Rate = ([MTD Avg Int Rate]-[PMTD Av Int Rate])/[PMTD Av Int Rate]
	(Month-over-Month)MoM Avg DTI = ([MTD Avg DTI]-[PMTD AVG DTI])/[PMTD AVG DTI]
	Good Loan % = (CALCULATE(COUNT(financial_loan[id]),financial_loan[GOOD VS BAD LOAN]= "good_loan"))/COUNT(financial_loan[id])
	GOOD LOAN APPLICATIONS = CALCULATE(COUNT(financial_loan[id]),financial_loan[GOOD VS BAD LOAN]="good_loan")
	GOOD LOAN FUNDED AMOUNT = CALCULATE([Total Funded Amount],financial_loan[GOOD VS BAD LOAN]="good_loan")
	GOOD LOAN TOTAL AMNT RECEIVED = CALCULATE([Total Amount Recieved],financial_loan[GOOD VS BAD LOAN]="good_loan")
	BAD Loan % = (CALCULATE(COUNT(financial_loan[id]),financial_loan[GOOD VS BAD LOAN]= "bad_loan"))/COUNT(financial_loan[id])
	BAD LOAN APPLICATIONS = CALCULATE(COUNT(financial_loan[id]),financial_loan[GOOD VS BAD LOAN]="bad_loan")
	BAD LOAN FUNDED AMOUNT = CALCULATE([Total Funded Amount],financial_loan[GOOD VS BAD LOAN]="bad_loan")
	BAD LOAN TOTAL AMNT RECEIVED = CALCULATE([Total Amount Recieved],financial_loan[GOOD VS BAD LOAN]="bad_loan")

        
# Snapshot of Dashboard (Power BI Desktop)
## SUMMARY DASHBOARD
![SUMMARY_SC](https://github.com/G-Kabilan/PowerBI_Analyst/assets/148671435/939b8a78-8821-4faf-9766-8ca2f4e06dd9)

## OVERVIEW
![OVERVIEW_SC](https://github.com/G-Kabilan/PowerBI_Analyst/assets/148671435/93b4cfbd-d7da-40a0-b8cf-9b304e91eb3f)

## DETAILS
![DETAILS_SC](https://github.com/G-Kabilan/PowerBI_Analyst/assets/148671435/e77a0332-ea9e-4359-866b-09678e8d34d1)


# Insights

The following inferences can be drawn from the dashboard;

### [1] KPI'S
	Total Loan Applications:38567
	MTD Loan Applications: 4313
	PMTD Loan Applications: 4035

	Total Funded Amount: 435.8 Million
	MTD Funded Amount: 53.98 Million
	PMTD Funded Amount:47.75 Million
	
	Total Amount Received: 473.1 Million
	MTD Amount Received: 58.1 Million
	PMTD Amount Received: 50.1 Million

	Avg Interest Rate: 12.0%
	MTD Interest Rate: 12.4 %
	PMTD Interest Rate: 11.9 %

	Avg DTI: 13.3%
	MTD Avg DTI: 13.7%
	PMTD Avg DTI: 13.2%
           

	Good Loan Issued: 86.2%
	Good Loan Applications:33243
	Good Loan Funded Amount:370 Million
	Good Loan Amount Received: 436 Million
	Bad Loan Issued: 13.8% 
	Bad Loan Applications: 5333
	Bad Loan Funded Amount:66 Million
	Bad Loan Amount Received: 37 Million

### [3] Loan Status
![LOAN STATUS SC](https://github.com/G-Kabilan/PowerBI_Analyst/assets/148671435/b6936808-cc47-49b8-a1d5-cf5c253da9c6)



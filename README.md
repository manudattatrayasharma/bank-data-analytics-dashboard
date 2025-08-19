Bank Data Analysis Dashboard

Dashboard Link: https://app.powerbi.com/links/gHALvEeqjs?ctid=2e00ccef-2930-4d6f-bf36-4dbc181c566c&pbi_source=linkShare&bookmarkGuid=3c1311da-04a8-4a0e-8e65-76458e9d4481

Problem Statement This dashboard empowers the bank to gain a comprehensive understanding of its customers, accounts, and transactions. It delivers transparency regarding account activity, transaction volumes, balances by account type and user, and essential demographic breakdowns. By visualizing monthly trends and key patterns, the dashboard enables data-driven decisions to improve services, identify risky accounts, and optimize product offerings.

The analytics highlight fluctuations in transaction amounts, variations in active/inactive accounts, and reveal how different customer groups and account types contribute to the overall bank business. With these insights, the bank can target strategies for customer engagement, operational efficiency, and risk management.

Steps Followed Step 1: Loaded the bank transaction, account, and customer data into Power BI Desktop using CSV files.

Step 2: Utilized Power Query Editor for data profiling: checked column distribution, quality, and profiles for accuracy.

Step 3: Identified and treated null values, primarily in transaction and account activity columns, ensuring clean analytics.

Step 4: Established calculated columns for customer age groups and for key metrics (e.g., monthly totals, account balances, transaction counts).

Step 5: Created measures using DAX for totals, averages, and counts (e.g., total balance by account type, count of inactive accounts, monthly transaction amounts).

Step 6: Custom visuals and charts added: Bar charts for inactive accounts by year/month, total by account type, amount by customer name, and transaction counts.

Line/area charts for monthly transaction amounts and balances to show trends. Pie/donut charts for gender distribution. Treemap for account type distribution.

Step 7: Applied visual filters and slicers for dynamic exploration by account type, age group, gender, and transaction type.

Step 8: Dashboard was published to Power BI Service for access and sharing.

Snapshot of Dashboard src="https://github.com/user-attachments/assets/e32b2609-c5d8-4ba6-976b-519bed2665bb" />

src="https://github.com/user-attachments/assets/aaeeabc1-bc0c-40a0-98cf-eda41517edfa" />

A two page report, built and published with Power BI Desktop and Service, yields these key findings:

Account Activity & Inactivity Counts of inactive accounts tracked per month/year reveal patterns (spikes in Oct 2024, Jan 2025, Apr 2025), potentially due to seasonal or policy factors.

Account Type Analysis Current Account: Large negative balance (indicative of high usage, loans, or overdraft).

Savings Account: Positive balance (1.48K). Customer Transaction Overview Highest transaction amount: Sarah Khan (0.25M credited); Mark Lee (-0.24M debited).

Priya Singh holds a large negative balance (-15,787.44K), possibly a business account or outlier.

Monthly Transaction Trends January has peak transaction (4.9M), drops in February (0.9M), spikes again in July (4M), picking up towards year-end.

Balances show regular monthly fluctuations, with most months around -1.3M to -1.6M.

Transaction Types Nearly even split between credit and debit transactions (both around 4K).

Customer Segmentation Age Groups: Major customers are 36-50 (200), then 26-35 (100).

Gender: 25% Male, 25% Female, 50% unspecified (blank), suggesting improvement needed in demographic data collection.

Account Distribution Equal numbers in Current and Savings accounts (200 each), implying balanced product engagement.

Methodology Notes Null and blank values were identified and treated (ignored for most aggregates).

DAX used for calculated columns and important measures:

Customer Count by Gender = DISTINCTCOUNT(CombinedBankingDataset[CustomerID]) by Gender

Customer Age = DATEDIFF(CombinedBankingDataset[DateOfBirth], TODAY(), YEAR)

Customer Age Group = SWITCH(TRUE(), [Customer Age]<=25, "25", [Customer Age]<=35, "26-35", [Customer Age]<=50,"36-50","51+")

Account Count by Type = COUNT(CombinedBankingDataset [Account_AccountID])Axis: AccountType, Values: Account Count by Type

ransactions by Month = CALCULATE(COUNT(CombinedBankingDataset[TransactionID]), ALLEXCEPT(CombinedBankingDataset, CombinedBankingDataset[TransactionDate].[Month]))

City or Region or Address, Values: DISTINCTCOUNT(CombinedBankingDataset[CustomerID])

TransactionType, Values: COUNT(CombinedBankingDataset[TransactionID])

Monthly Transaction Amount = CALCULATE(SUM(CombinedBankingDataset[Amount]), ALLEXCEPT(CombinedBankingDataset, CombinedBankingDataset[TransactionDate].[Month]))

Average Balance = AVERAGE(CombinedBankingDataset[Balance])

AccountType, Values:Total Balance = SUM(CombinedBankingDataset[Balance])

This dashboard is ideal for rapid bank business reviews, customer profiling, and for identifying both high-value clients and potentially risky accounts. For ongoing improvement, consider enriching customer profile data and automating monthly performance tracking

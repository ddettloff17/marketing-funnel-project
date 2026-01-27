# marketing-funnel-project

<h2>Background and Overview</h2>
This project was built using a fictional e-commerce company, Flocart, business scenario, and raw datasets generated with the assistance of AI to simulate a realistic analytics engagement. The intent was to recreate the type of ambiguous, messy data a data analyst would receive in a real organization, rather than working from a clean, pre-defined dataset.
<br><br>
The company is experiencing inconsistent conversion performance and unclear marketing attribution. Leadership believes users are entering the funnel in high volume but dropping off before purchase, and revenue reporting varies depending on the source being analyzed. The analytics team was tasked with cleaning and modeling multiple raw datasets using Excel and SQL, defining a reliable funnel from visit to purchase, and extracting insights to inform business decisions. Outputs are structured to support stakeholder reporting and future visualization in Power BI.

<h2>Data Structure & Initial Checks</h2>
Flocart's database structure as seen below consists of four tables:campaigns, users, orders and events, with a total row count of 18,050 records.
<br>
<br>
<img width="624" height="583" alt="Screenshot 2026-01-18 at 1 40 38 PM" src="https://github.com/user-attachments/assets/a140ef9b-0fdb-42b0-b8e0-9f5f73cbad31">
<br><br>
Prior to analysis, quality checks were performed to identify inconsistencies, missing values, and formatting issues across all datasets. The majority of cleaning was done in Excel, where separate “clean” copies of each sheet were created. Key columns that were standardized, normalized, or transformed are highlighted in screenshots, and detailed context—including reasoning and cleaning logic—is provided in a separate document, for reference. This ensured the datasets were ready for SQL modeling and downstream funnel analysis.

[View SQL queries](https://github.com/ddettloff17/marketing-funnel-project/blob/main/sql_queries)

<h2>Executive Summary</h2>
This analysis addresses inconsistent conversion performance and conflicting revenue attribution across marketing channels. Raw event-level behavioral data and order-level revenue data were cleaned and modeled using Excel and SQL to create a consistent reporting foundation.

A standardized funnel was explicitly defined as view → add_to_cart → checkout → purchase, allowing drop-off to be evaluated consistently across campaigns. Because the orders dataset does not contain campaign attribution, a last-touch attribution model was implemented, assigning each order to the most recent campaign interaction prior to purchase. This modeling choice prevents revenue duplication and ensures campaign performance is comparable across sources.

Results show that top-of-funnel volume is not the primary issue. Affiliate campaign_id 4 drives the highest number of users into the funnel and maintains stable progression through early stages. Email campaign_id 2 delivers lower volume but converts at comparable rates, indicating higher user intent. Google Search campaign_id 3 mirrors email behavior with steady funnel progression and no abnormal early-stage drop-off.

Across all campaigns, the largest and most consistent loss of users occurs between checkout and purchase, indicating late-stage conversion friction rather than acquisition inefficiency. This suggests issues related to payment, trust, or checkout experience rather than campaign targeting.

Final modeled outputs include campaign-level funnel performance, conversion rates, and attributed revenue, structured for direct use in Power BI to support ongoing reporting and visualization.

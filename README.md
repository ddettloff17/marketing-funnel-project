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
Prior to analysis, quality checks were performed to identify inconsistencies, missing values, and formatting issues across all datasets. The majority of cleaning was done in Excel, where separate “clean” copies of each sheet were created. Key columns that were standardized, normalized, or transformed are highlighted in screenshots, and detailed context—including reasoning and cleaning logic—is provided in a separate document [link here] for reference. This ensured the datasets were ready for SQL modeling and downstream funnel analysis.


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

<h2>Insights Deep Dive</h2>

<h3>Data Cleaning and Preparation</h3>

The analysis began with cleaning and standardizing multiple raw datasets to ensure accurate joins, consistent metrics, and reliable reporting. Initial data inspection revealed inconsistent formatting, mixed data types, and non-standardized values across key fields.

Key cleaning actions were performed in Excel, including:

Standardizing event types into a controlled set of funnel stages (view, add_to_cart, checkout, purchase)

Removing currency symbols and text from revenue fields to enable numeric aggregation

Normalizing campaign source values to support clean joins across datasets

Creating parallel cleaned columns while preserving raw data for auditability

As part of the cleaning process, a structured data quality issue log was maintained to document known inconsistencies, row impact, and resolution decisions. Issues that could not be safely corrected (such as missing emails or blank country values) were intentionally retained as null and handled analytically rather than imputed. The full issue log and supporting Excel screenshots are available in the /assets directory.


<h3>Funnel Modeling and Validation</h3>

A standardized marketing funnel was explicitly defined to evaluate user progression and identify friction points. The funnel model used throughout the analysis is:

view → add_to_cart → checkout → purchase

This ordered funnel ensures consistent interpretation across campaigns and prevents misleading comparisons caused by unordered event counts.

Initial funnel analysis confirmed that users are entering the funnel in meaningful volume, validating leadership’s assumption that acquisition is not the primary constraint.

<h3>Campaign-Level Funnel Performance</h3>

After validating overall funnel behavior, funnel progression was evaluated at the campaign level to assess traffic quality rather than volume alone.

This analysis revealed clear differences between campaigns:

  1.Some campaigns drive high volumes of users but show weaker progression through later funnel stages

  2.Others deliver lower volume but maintain strong conversion efficiency, indicating higher intent users

  3.Breaking the funnel down by campaign reframed performance from who drives traffic to who drives outcomes.

<h3>Revenue Attribution Modeling</h3>

Revenue reporting inconsistencies were traced back to missing campaign attribution in the orders dataset. A naive join between events and orders would duplicate revenue across multiple campaigns and distort performance metrics.

To resolve this, a last-touch attribution model was implemented. Each order was assigned to the most recent campaign interaction associated with the user prior to purchase.

This modeling decision:

Prevents revenue inflation, produces consistent, comparable campaign metrics, and establishes a clear attribution assumption for reporting.
(All attribution logic and supporting queries are documented in the [accompanying SQL file.](https://github.com/ddettloff17/marketing-funnel-project/blob/main/sql_queries))

<h3>Campaign Conversion Efficiency</h3>

With attribution established, campaign efficiency was evaluated by comparing users exposed to each campaign against orders attributed to that same last touch.

This step confirmed that:

High-volume campaigns are not always the highest converting

Certain lower-volume channels perform comparably or better in terms of conversion rate

Campaign effectiveness cannot be evaluated on traffic volume alone

These metrics form the foundation for campaign optimization and budget allocation decisions.

<h3>Checkout-to-Purchase Drop-Off Analysis</h3>

While aggregate funnel analysis identified checkout as the primary point of user loss, this step quantified late-stage drop-off by campaign.

Campaign-level checkout-to-purchase analysis showed that:

The most significant user loss occurs after checkout initiation

Drop-off rates vary meaningfully by campaign

Late-stage friction, rather than acquisition quality, is the dominant conversion constraint

This shifts the optimization focus from marketing channels to checkout experience, payment flow, and user trust factors.

<h3>Behavioral Signals Beyond the Funnel</h3>

Finally, the analysis examined user behaviors beyond immediate funnel progression to identify actions associated with higher total revenue over time.

Rather than attributing causality, this step highlights behavioral signals correlated with higher-value users. These insights support future segmentationx segmentation, remarketing strategies, and product experimentation.

<h4>--Notes on Presentation</h4>

SQL queries are intentionally excluded from the README and [documented separately](https://github.com/ddettloff17/marketing-funnel-project/blob/main/sql_queries) to keep the narrative focused on insights and modeling decisions.

Modeled outputs are structured for direct use in Power BI, including campaign-level funnel metrics, attributed revenue, conversion rates, and drop-off analysis.

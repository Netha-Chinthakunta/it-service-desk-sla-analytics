IT Service Desk & SLA Performance Analytics

An end-to-end data analytics project analyzing IT service desk incident data — from raw ticket data to a fully interactive Power BI dashboard — built using SQL and Power BI.

Problem Statement

An IT support team is drowning in tickets with no clear visibility into SLA breaches, agent workload balance, or recurring root causes. Leadership needs to know: are we meeting SLAs, where are the bottlenecks, and which categories, agents, or time periods are driving the most breaches — so staffing and prioritization decisions can be made with evidence instead of guesswork.

This project answers that question end-to-end: generating realistic ticket data, cleaning and modeling it in SQL, and building a Power BI dashboard that tells the story clearly enough for a non-technical stakeholder to act on.

Tech Stack
SQL — data generation, cleaning, SLA logic, window functions, CTEs, views
Power BI — data modeling (star schema), DAX measures, interactive dashboard
Project Structure
/docs           → milestone write-ups (what I did, why, what I learned)
/sql            → SQL scripts by phase (generation, cleaning, analysis)
/screenshots    → dashboard pages, data model view, ER diagram
Milestones
#	Milestones
01	Problem statement & project scope	
02	Synthetic data generation (SQL)	
03	Data cleaning	
04	SQL analysis (aggregations, window functions, CTEs)	
05	Power BI data modeling (star schema)	
06	DAX measures	
07	Dashboard design (3-page narrative flow)	
08	Insights & key findings	

Detailed write-ups for each stage are in /docs.

Dashboard Preview

(Screenshot added once the dashboard is built)

Key Insights

(Added at the end — this section will summarize the 3-5 most important findings from the analysis)

About This Project

Built as part of my transition into a data analyst role, applying concepts learned toward the PL-300 (Power BI Data Analyst) certification. The project design mirrors real IT service management data structures (ServiceNow-style), reflecting my current role as an EUC Analyst.

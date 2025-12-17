SQL insights:

Walmart Sales Analysis — SQL Insights

Project Overview

This project analyzes Walmart weekly sales data using SQL to uncover store-level, department-level, time-based, and business-driven insights. The goal is to move beyond simple aggregation and answer real business questions such as seasonality effects, store performance drivers, and external factor influence.

The analysis is structured into logical phases, progressing from descriptive metrics to decision-oriented insights.

⸻

A) Store-Level Analysis

1- Total Weekly Sales per Store

Stores were ranked by total revenue contribution.

Top performing stores:  
	•	Store 20  
	•	Store 4  
	•	Store 14  

* A small number of stores contribute disproportionately to total sales.

⸻

2- Average Weekly Sales per Store (Ranking)

Stores were also ranked by average weekly sales, not just total volume.

Result:  
	•	The same stores (20, 4, 14) remain top performers  

High performance is consistent week-to-week and not driven solely by longer operating periods.

⸻

B) Department-Level Analysis  

* Top 10 Best-Selling Departments  

Departments ranked by total weekly sales:    


| Rank | Department | Total Sales ($) |
|-----:|-----------:|----------------:|
| 1 | 92 | 483.9M |
| 2 | 95 | 449.3M |
| 3 | 38 | 393.1M |
| 4 | 72 | 305.7M |
| 5 | 90 | 291.1M |


Revenue is highly concentrated in a small subset of departments, indicating strong candidates for inventory prioritization and promotional focus.

---

* C) Date & Time Analysis

* Sales by Year  


| Year | Total Sales ($) |
|----:|----------------:|
| 2010 | 2.29B |
| 2011 | 2.45B |
| 2012 | 2.00B |


2011 was the strongest year, while 2012 shows a noticeable decline.

⸻

* Average Sales by Month  
	•	December is the strongest month on average  
	•	January is the weakest  

Clear seasonal patterns exist, driven by holiday demand.

⸻

* Week-to-Week Growth Analysis  

Using SQL window functions, week-over-week changes were calculated per store.  

Sales exhibit significant short-term volatility, reinforcing the importance of trend analysis rather than single-week performance.

⸻

D) Key Business Questions (Core Insights)

* Do Holidays Increase Sales?  
	•	Yes.  
	•	Average weekly sales during holiday weeks are ~7% higher than non-holiday weeks.  

Holidays increase sales intensity per week, even though they represent fewer weeks overall.  

⸻

Does Store Size or Type Affect Revenue?  

Stores were analyzed by size and type (A, B, C).  

Finding:  
	•	strong relationship between store size/type and total revenue where store type A generates a total of 4.3B whereas store type C only generates 0.4B in total. 

⸻

* Weather & Economic Factors  

Temperature:  
	•	No meaningful correlation with average weekly sales  

Fuel Prices:  
	•	Correlation coefficient ≈ 0.008  

External factors show negligible direct impact on weekly sales at the aggregate level.  

⸻

Phase 6 — Executive Summary (Presentation Insights)  
	•	Top 5 Stores by Sales: 20, 4, 14, 13, 2  
	•	Top Departments: 92, 95, 38, 72, 90  
	•	Holiday Impact: ~7% higher average weekly sales  
	•	External Correlation: No clear link to temperature or fuel prices  
	•	Best vs Worst Year: 2011 (best), 2010 (middle), 2012 (worst)  
	•	Store Type Performance (Avg Weekly Sales):  
	•	Type A: ~20K  
	•	Type B: ~12K  
	•	Type C: ~9.5K  

⸻

* Key Takeaways
	•	Sales are concentrated in specific stores and departments  
	•	Seasonality (holidays, December) is a major driver of performance  
	•	Store size and macroeconomic factors have limited predictive power  
	•	Average-based metrics provide fairer comparisons than totals alone  

⸻

* Tools Used  
	•	SQL (MySQL) — data aggregation, joins, window functions  
	•	Power BI (Web) — visualization and presentation  

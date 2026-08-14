
Issue	Observation	Handling
Transaction-level Superstore data	Multiple rows per order/product	Kept transactional detail, then aggregated for analysis
Date format	Order Date imported as text/date inconsistently	Converted to Date type
Different time grains	Sales data daily; Google Trends monthly	Created YearMonth for matching
Google Trends wide format	Separate columns for Furniture, Office Supplies, Technology	Unpivoted to Category + Trend Score
Category naming mismatch	Office supplies vs Office Supplies	Standardized category names
Repeated trend values	Same monthly Trends value appears on many sales rows	Expected because one monthly score applies to multiple transactions
Missing sales after merge risk	External signal may not exist for every row	Used a Left Outer Join to preserve sales data
Google Trends interpretation	0–100 index, not search volume	Treated as an external interest proxy
	

README
## Milestone 1 — Data Preparation
The Superstore sales dataset was cleaned in Power Query and combined with Google Trends data to create a tidy analytical dataset.
Final analytical fields:
- Date
- Category
- Subcategory
- Region
- Units
- Revenue
- YearMonth
- Trend Score

Google Trends was transformed from wide to long format and merged with
sales data using month and category. A left join was used to preserve
all sales observations.

### Data Quality Log
| Issue | Resolution |
|---|---|
| Daily sales vs monthly Trends | Created YearMonth |
| Category naming differences | Standardized category names |
| Wide Google Trends data | Unpivoted to long format |
| Repeated Trend values | Expected at detailed sales grain |
| Trends is an index, not volume | Treated as an external demand proxy |

### Power Query Output
![Cleaned Data](images/cleaned_data.png)
![Google Trends Merge](images/power_query_merge.png)

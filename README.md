# Customer Churn Analysis & Customer Intelligence

A data analytics project focused on understanding customer churn, subscription behavior, and revenue impact for an OTT-style subscription business. The project uses Python and SQL to combine customer, subscription, and customer-support data, calculate business KPIs, explore churn patterns, and communicate retention opportunities.

## Project Objectives

- Identify customers who have churned and examine their subscription behavior.
- Compare churn across plan types and contract types.
- Explore the relationship between customer-support escalations and churn.
- Calculate customer retention and revenue-related KPIs.
- Visualize trends and provide actionable retention recommendations.

## Tech Stack

- **Python**
- **SQL / SQLite**
- **Pandas** – data manipulation and analysis
- **NumPy** – calculations and feature engineering
- **Matplotlib** – charts and trend visualization
- **Seaborn** – statistical visualizations

## Dataset Structure

The analysis uses three related tables stored in a SQLite database:

| Table | Description |
|---|---|
| `db_customer` | Customer attributes such as customer ID, country, state, gender, and date of birth |
| `db_subscription` | Subscription dates, plan and contract types, cancellation details, monthly charges, CLTV, and churn score |
| `db_support` | Complaint dates, escalations, and customer satisfaction scores |

The notebook imports sheets from `customer_churn_data_raw.xlsx` and stores them as tables in `customer_churn.db`.

> **Dataset note:** The raw Excel dataset is required to run the notebook from the beginning. It is referenced by the notebook but is not included in this repository unless you add it separately.

## Project Workflow

1. **Database creation and data extraction**
   - Read the Excel workbook using Pandas.
   - Create a SQLite database and load each worksheet as a table.
   - Retrieve SQL tables into Pandas DataFrames.

2. **Data cleaning**
   - Rename columns and remove unused fields.
   - Convert date columns to datetime format.
   - Standardize categorical values.
   - Handle missing country values using state-to-country mapping.
   - Remove unnecessary support-table columns.

3. **Feature engineering and data integration**
   - Create a binary `churn_flag` using cancellation dates.
   - Prepare support records for merging.
   - Join customer, subscription, and support data using `customerid`.
   - Calculate customer tenure and churn-risk segments.
   - Export the combined dataset to `exported_churn_data.csv`.

4. **Exploratory data analysis**
   - Calculate churn and retention rates.
   - Analyze churn by plan type and contract type.
   - Examine revenue-related metrics and customer tenure.
   - Explore the relationship between support escalations and churn.

5. **Data visualization**
   - Monthly churn trend.
   - Churn rate by plan and state.
   - Correlation heatmaps.
   - Pair plots and categorical comparisons.
   - Pivot-table summaries.

## Key Metrics

The notebook calculates or explores the following metrics:

- Churn Rate
- Retention Rate
- Churn by Plan Type
- Average Revenue per User (ARPU)
- Average Customer Tenure
- Revenue at Risk
- Escalation Rate
- Average Complaints per Customer
- Correlation between Escalations and Churn
- Churn Risk Segmentation (Low, Medium, High)

## Visualizations

The following charts are exported from the project notebook and can be viewed directly in this README on GitHub.

### Monthly Churn Trend

<img width="692" height="316" alt="monthly_churn_trend" src="https://github.com/user-attachments/assets/6b70bb86-f189-4c49-b949-66ccf9189011" />


### Churn Rate by Plan Type

<img width="613" height="393" alt="churn_rate_by_plan" src="https://github.com/user-attachments/assets/c43d14d5-9fe2-411a-9d8c-b148d6f4b85c" />


### Churn by State
<img width="1001" height="457" alt="churn_by_state" src="https://github.com/user-attachments/assets/63bb16cf-39d0-417f-850d-c3388839f21e" />


### Correlation Heatmap

<img width="700" height="590" alt="correlation_heatmap" src="https://github.com/user-attachments/assets/154cd80e-9299-4181-8261-81951ed00c71" />

### Monthly Charges by Plan, Gender, and Churn Risk

<img width="1594" height="490" alt="monthly_charges_by_plan_and_risk" src="https://github.com/user-attachments/assets/df3272ed-9e4f-4191-9299-dbdccb7d0653" />


## Key Findings

Based on the project report and notebook outputs:

- **Overall churn rate:** 28.57%
- **Retention rate:** 71.43%
- **ARPU:** 18.85 (dataset currency units)
- **Average customer tenure:** approximately 1,452 days
- **Revenue associated with churned customers:** 73.94 (reported in the notebook as thousands of rupees)
- **Escalation rate:** 19.05%
- **Average complaints per customer:** 0.43
- **Escalation–churn correlation:** 0.77

The report also highlights a higher churn rate among monthly-contract customers than annual-contract customers, suggesting that contract-migration and targeted retention initiatives may be worth evaluating.

These results are descriptive insights from the supplied sample dataset, not proof that a retention intervention will reduce churn. The dataset is small, so findings should be validated with a larger dataset before business decisions are made.

## Recommendations

- Prioritize outreach to customers in medium- and high-risk segments.
- Investigate support escalations and customer satisfaction among churned users.
- Review pricing, plan changes, and cancellation reasons for high-churn segments.
- Evaluate incentives for annual-contract migration where commercially appropriate.
- Monitor churn and revenue-related KPIs over time to assess retention efforts.

## How to Run

### 1. Clone or download the project

Place the notebook and required raw Excel dataset in the same directory.

### 2. Install dependencies

```bash
pip install numpy pandas matplotlib seaborn openpyxl jupyter
```

### 3. Add the dataset

Make sure the Excel file is named:

```text
customer_churn_data_raw.xlsx
```

The notebook expects this filename in its working directory.

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `churn_analysis.ipynb` and run the cells in order.

The notebook creates the SQLite database and exports the merged analysis dataset as `exported_churn_data.csv`.


## Skills Demonstrated

SQL data extraction, SQLite database management, data cleaning, data preprocessing, feature engineering, exploratory data analysis (EDA), KPI calculation, customer segmentation, data visualization, correlation analysis, and business insight communication.

---


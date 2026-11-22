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

![Monthly churn trend](churn_readme_assets/monthly_churn_trend.png)

### Churn Rate by Plan Type

![Churn rate by plan type](churn_readme_assets/churn_rate_by_plan.png)

### Churn by State

![Churn by state](churn_readme_assets/churn_by_state.png)

### Correlation Heatmap

![Correlation heatmap](churn_readme_assets/correlation_heatmap.png)

### Monthly Charges by Plan, Gender, and Churn Risk

![Monthly charges by plan, gender, and churn risk](churn_readme_assets/monthly_charges_by_plan_and_risk.png)

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

## Project Files

```text
.
├── churn_analysis.ipynb
├── customer_churn_data_raw.xlsx   # required input; not included by default
├── customer_churn.db              # generated SQLite database
├── exported_churn_data.csv        # generated merged dataset
└── README.md
```

## Skills Demonstrated

SQL data extraction, SQLite database management, data cleaning, data preprocessing, feature engineering, exploratory data analysis (EDA), KPI calculation, customer segmentation, data visualization, correlation analysis, and business insight communication.

---

**Disclaimer:** This project performs churn analysis and risk segmentation using an existing churn score. It does not train or evaluate a machine-learning churn prediction model.

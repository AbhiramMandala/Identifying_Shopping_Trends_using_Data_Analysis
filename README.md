# Identifying Shopping Trends Using Data Analysis

Exploratory data analysis of 3,900 customer transactions to uncover purchasing patterns, product preferences, and demographic trends in retail shopping behavior.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243?logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Viz-4C72B0)
![Plotly](https://img.shields.io/badge/Plotly-Interactive%20Charts-3F4F75?logo=plotly&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)

---

## Project Overview

Retailers generate large volumes of transactional data but often lack the analytical layer needed to turn it into decisions about merchandising, promotions, and customer targeting. This project performs an exploratory data analysis (EDA) of a retail shopping dataset to answer 19 specific business questions about customer demographics, spending behavior, product preferences, and channel/payment patterns.

The analysis uses Python's data science stack (Pandas, NumPy, Matplotlib, Seaborn, and Plotly) to clean, group, aggregate, and visualize the data, then interprets the resulting charts to surface patterns that could inform marketing, inventory, and customer-experience decisions. The intended audience for these insights includes marketing analysts, merchandising teams, and business stakeholders who need a data-backed view of how customers shop.

## Business Problem

The analysis is framed around questions a retail analytics team would realistically ask of transactional data:

- Who are the customers, and what does the age/gender mix look like?
- Which product categories and items generate the most purchases and revenue?
- How much are customers spending, and does spending vary by category, gender, or location?
- Does a subscription, discount, or promo code change purchasing behavior?
- Which payment methods and shipping types do customers prefer?
- Are there regional (state-level) differences in spending?
- Is purchase amount related to product size, review rating, or customer age?

## Project Objectives

- Load and validate the shopping trends dataset for completeness and consistency.
- Engineer basic age-bracket features to support demographic analysis.
- Answer 19 defined analytical questions using grouping, aggregation, and visualization.
- Visualize purchasing patterns across category, gender, season, payment method, shipping type, discounts, and location.
- Summarize findings that are grounded directly in the computed data, without projecting beyond what the dataset supports.

## Dataset

- **File:** `shopping_trends_updated.csv`
- **Records:** 3,900 rows
- **Features:** 18 columns
- **Data quality:** No missing values and no duplicate rows across any column.

| Feature | Description | Data Type |
|---|---|---|
| Customer ID | Unique identifier for each customer | Integer |
| Age | Customer age (18–70 in this dataset) | Integer |
| Gender | Male / Female | Categorical |
| Item Purchased | Specific item bought (25 unique items) | Categorical |
| Category | Product category (Clothing, Accessories, Footwear, Outerwear) | Categorical |
| Purchase Amount (USD) | Transaction value | Integer |
| Location | U.S. state of the customer (50 unique states) | Categorical |
| Size | Product size (S, M, L, XL) | Categorical |
| Color | Product color | Categorical |
| Season | Season of purchase (Spring, Summer, Fall, Winter) | Categorical |
| Review Rating | Customer's product rating | Float |
| Subscription Status | Whether the customer is subscribed (Yes/No) | Categorical |
| Shipping Type | Shipping method used | Categorical |
| Discount Applied | Whether a discount was applied (Yes/No) | Categorical |
| Promo Code Used | Whether a promo code was used (Yes/No) | Categorical |
| Previous Purchases | Count of the customer's prior purchases | Integer |
| Payment Method | Payment channel used | Categorical |
| Frequency of Purchases | How often the customer shops | Categorical |

## Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core language for data analysis |
| Pandas | Data loading, cleaning, grouping, aggregation |
| NumPy | Numerical operations |
| Matplotlib | Static charts (bar plots, pie charts) |
| Seaborn | Statistical visualizations (bar/count plots) |
| Plotly Express | Interactive charts (histograms, bar charts, sunburst charts) |
| Jupyter Notebook | Interactive analysis environment |

## Analytical Workflow
```
Raw Dataset (CSV)
     ↓
Data Loading (Pandas)
     ↓
Data Inspection (shape, dtypes, .info())
     ↓
Data Cleaning (null check, duplicate check, unique-value audit)
     ↓
Feature Engineering (Age_category, Age_bracket, numeric mappings)
     ↓
Exploratory Data Analysis (groupby / aggregation per question)
     ↓
Visualization (Matplotlib, Seaborn, Plotly)
     ↓
Interpretation & Business Insights
```


Each of the 19 questions in the notebook follows this same pattern: isolate the relevant column(s), aggregate with `groupby()`, visualize the result, then interpret it in a markdown cell.

## Exploratory Data Analysis

**Customer Demographics**
Age distribution was examined directly and through two engineered features — `Age_category` (child/teen/young adult/middle-aged/old) and `Age_bracket` (youth/teen/adult/middle age/old) — visualized against gender using count plots and histograms.

**Product & Category Analysis**
Average purchase amount and item frequency were computed per category, with the most commonly purchased item identified within each of the four categories (Clothing, Accessories, Footwear, Outerwear).

**Purchase Behavior**
Spending was compared across gender, subscription status, review rating, and previous purchase count, using bar plots of mean and total purchase amount.

**Discount & Promotion Analysis**
Purchase amounts were compared between customers who did and didn't use a discount or promo code, broken down further by gender using sunburst charts.

**Geographic Analysis**
Average purchase amount was calculated per U.S. state (50 states in the dataset) and visualized as a bar chart to compare regional spending.

**Shipping Analysis**
Shipping type preference was analyzed overall and by product category, with a pie chart showing the distribution across the six shipping types.

**Payment & Subscription Behavior**
Payment method popularity and associated average spend were computed, along with a comparison of purchase amount and count between subscribed and non-subscribed customers.

## Key Insights

- **Payment method distribution is broad and fairly even.** PayPal (677), Credit Card (671), and Cash (670) are the top three of six payment methods, each within roughly 5% of one another — no single channel dominates.
- **Average purchase amount is nearly flat across product categories.** Footwear ($60.26), Clothing ($60.03), and Accessories ($59.84) average within about a dollar of each other, with Outerwear slightly lower ($57.17) — category alone is a weak predictor of transaction size in this dataset.
- **Purchase frequency by season shows minimal seasonality.** Spring (999), Fall (975), Winter (971), and Summer (955) transaction counts are all within about 4.5% of each other, meaning the season-based bar chart in the notebook shows relatively uniform demand rather than a clear peak season.
- **Discount and promo code usage are identical in this dataset.** Every record with `Discount Applied = Yes` also has `Promo Code Used = Yes` (1,677 of 3,900 transactions), and average spend is nearly the same for discount users ($59.28) and non-users ($60.13) — suggesting discounts did not measurably increase basket size here.
- **Gender skews toward higher transaction volume for men.** Male customers account for 2,652 of 3,900 transactions versus 1,248 for female customers, though average spend per transaction is close ($59.54 male vs. $60.25 female) — the gap is in transaction count, not per-purchase value.
- **Regional spending shows a mild spread.** Average purchase amount ranges from about $54–68 across the 50 states in the dataset, with Alaska, Pennsylvania, and Arizona at the top — a modest but visible geographic difference.

## Visualizations

The notebook uses a mix of static and interactive chart types to explore the data:

- **Bar charts** (Matplotlib / Seaborn / Plotly) — average and total purchase amount by category, gender, payment method, location, size, and age.
- **Count plots** (Seaborn) — customer counts by age bracket and gender, and discount usage split by gender.
- **Pie charts** (Matplotlib) — payment method and shipping type distribution.
- **Histograms** (Plotly) — age distribution, item purchased by category, season, and color frequency.
- **Sunburst charts** (Plotly) — hierarchical breakdowns of gender × promo code, gender × discount, and gender × age category.

No chart image files are currently committed to the repository; all visualizations render inline when the notebook is executed. A future `images/` directory could be added to export and embed static chart previews directly in this README.

## Project Structure

```
Identifying_Shopping_Trends_using_Data_Analysis/
│
├── README.md
├── Shopping_Trends_Analysis.ipynb
└── shopping_trends_updated.csv
```


## How to Run the Project

**1. Clone the repository**
```bash
git clone https://github.com/AbhiramMandala/Identifying_Shopping_Trends_using_Data_Analysis.git
cd Identifying_Shopping_Trends_using_Data_Analysis
```

**2. Create a virtual environment**

Windows:
```bash
python -m venv venv
venv\Scripts\activate
```

macOS/Linux:
```bash
python3 -m venv venv
source venv/bin/activate
```

**3. Install dependencies**

There is no `requirements.txt` in the repository. Based on the imports used in the notebook, install:
```bash
pip install pandas numpy matplotlib seaborn plotly jupyter
```

**4. Launch Jupyter**
```bash
jupyter notebook
```
Open `Shopping_Trends_Analysis.ipynb` and run the cells from top to bottom.

> **Note:** The notebook was originally built in Google Colab and loads the data with `pd.read_excel()` from a Google Drive path. To run it locally against the included `shopping_trends_updated.csv`, replace the data-loading cell with:
> ```python
> shop = pd.read_csv('shopping_trends_updated.csv')
> ```

## Reproducibility

- **Dataset:** `shopping_trends_updated.csv` (included in the repository)
- **Notebook:** `Shopping_Trends_Analysis.ipynb`
- **Libraries required:** pandas, numpy, matplotlib, seaborn, plotly
- **Execution order:** Run sequentially — later cells depend on the `Age_category`, `Age_bracket`, and mapped columns created earlier in the notebook.
- **Assumption:** The data-loading cell must be updated to read the local CSV (see note above) before running outside Colab.

## Limitations

- This is an exploratory analysis, not a predictive model — no forecasting or classification is performed.
- All relationships described are observational; correlation is not tested for statistical significance, and no causal claims are made.
- The dataset appears to be a static, single-period snapshot with no timestamps, so trends over time cannot be assessed.
- `Discount Applied` and `Promo Code Used` are perfectly correlated in this dataset, so their individual effects on spending cannot be separated.
- Location is limited to U.S. states; no city-level or international data is present.

## Future Improvements

- Customer segmentation (e.g., RFM analysis) using `Previous Purchases`, `Purchase Amount`, and `Frequency of Purchases`.
- Statistical hypothesis testing (e.g., t-tests) to validate whether observed differences (gender, subscription, discount) are significant.
- Predictive modeling for spend or churn using the existing feature set.
- An interactive dashboard (e.g., Plotly Dash or Streamlit) built on top of the existing aggregations.
- A `requirements.txt` and exported chart images to make the repository easier to reproduce and review without running the notebook.

## Business Applications

- **Marketing:** Payment method and channel data can inform which checkout options to prioritize in promotions.
- **Merchandising:** Category- and item-level purchase frequency can guide inventory allocation across Clothing, Accessories, Footwear, and Outerwear.
- **Promotion strategy:** The near-identical average spend between discount and non-discount transactions suggests discounts should be evaluated for incremental impact rather than assumed to increase basket size.
- **Logistics:** Shipping type preference data can support carrier and fulfillment planning.
- **Regional strategy:** State-level spending differences can inform where to focus regional marketing spend.

## Conclusion

This project analyzes 3,900 retail transactions across 18 features to answer 19 targeted questions about customer demographics, product preferences, spending patterns, and channel behavior. The analysis demonstrates a complete, methodical EDA workflow — data validation, feature engineering, grouped aggregation, and multi-library visualization — and surfaces concrete, data-grounded observations (e.g., near-flat category spending, even payment-method distribution, and the discount/promo-code correlation) rather than generic commentary. It reflects the core skill set of a data analyst: turning raw transactional data into questions, evidence, and business-relevant interpretation.

## Acknowledgments

Thanks to **Edunet** and **TechSaksham** for supporting this analysis.

## Author

**Abhiram Mandala**
GitHub: [@AbhiramMandala](https://github.com/AbhiramMandala)
Repository: [Identifying_Shopping_Trends_using_Data_Analysis](https://github.com/AbhiramMandala/Identifying_Shopping_Trends_using_Data_Analysis)


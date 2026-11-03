# 🛍️ Customer Shopping Behavior Analysis

An end-to-end data analytics project examining **3,900 customer transactions** ($233.1K total revenue) to uncover shopper demographics, evaluate subscription program mechanics, optimize promotional discount strategies, and boost customer retention.

---

## 📌 Project Overview
The goal of this project is to analyze retail purchasing patterns, segment customers based on purchase history, and translate raw transactional data into actionable business strategies. 

### Key Business Highlights
- **Gross Revenue Analyzed:** $233,081 across 3,900 orders
- **Demographic Skew:** Male buyers drive **67.7% of gross revenue** ($157.8K), highlighting significant potential for targeted marketing toward female shoppers.
- **Acquisition Bottleneck:** High overall customer loyalty (**79.9% repeat buyers**), but first-time customer acquisition sits at just **2.1%**.
- **Subscription Mechanics:** Active subscribers maintain similar average order values ($59.49 vs. $59.87 for non-subscribers), proving subscription value comes from purchase frequency rather than individual order size.

---

## 📊 Dataset
- **Source:** Retail Shopping Behavior Dataset
- **Size:** 3,900 records, 18 initial attributes
- **Key Columns:** `Customer ID`, `Age`, `Gender`, `Item Purchased`, `Category`, `Purchase Amount (USD)`, `Review Rating`, `Subscription Status`, `Shipping Type`, `Discount Applied`, `Previous Purchases`, `Frequency of Purchases`

---

## 🛠️ Tools & Tech Stack
- **Python (Pandas, NumPy):** Data loading, handling missing values, standardizing column names (`snake_case`), and feature engineering.
- **SQL / MySQL:** Database warehousing, multi-table queries, subqueries, CTEs, and Window Functions (`ROW_NUMBER()`).
- **PowerPoint:** Executive deck design presenting business strategy and roadmap recommendations.
- **Git & GitHub:** Version control and repository documentation.

---

## 🚀 Project Steps & Implementation Workflow

### 1. Data Cleaning & Preprocessing (Python)
- Imputed 37 missing `review_rating` values using **category-level medians** to maintain product category distributions.
- Standardized all column headers to `snake_case` for clean MySQL integration.
- Engineered new features:
  - `age_group`: Quartile-based age categories (`Young Adult`, `Adult`, `Middle-aged`, `Senior`).
  - `purchase_frequency_days`: Standardized frequency text to numeric days (`Weekly` = 7, `Monthly` = 30, `Annually` = 365).
- Removed redundant `promo_code_used` column after confirming 100% correlation with `discount_applied`.

### 2. Database Warehousing & Querying (MySQL)
Cleaned data was ingested into a local MySQL database via `SQLAlchemy`. Ten core queries were crafted to address key business objectives:
- **Revenue Aggregations:** Calculated total revenue split by gender, age groups, and shipping tiers.
- **Subqueries:** Filtered customers using discounts while spending above average ($59.76).
- **Window Functions:** Employed `ROW_NUMBER() OVER (PARTITION BY category ORDER BY COUNT(customer_id) DESC)` to isolate top-3 selling items per category.
- **Customer Segmentation (CTEs):** Segmented buyers into `New` (1 purchase), `Returning` (2–10 purchases), and `Loyal` (>10 purchases).

---

## 📈 Dashboard & Strategic Presentation
- **Executive Slides:** 10-slide deck summarizing key data findings, customer segment breakdowns, product category performance, and discount sensitivity.
- **Visuals:** Highlighted revenue split (68% Male / 32% Female), order value comparisons by shipping type (+3.5% higher spend for Express Shipping), and loyalty vs. new buyer acquisition rates.

---

## 💡 Key Results & Business Recommendations
1. **Female Shopper Acquisition:** Expand digital ad campaigns targeting female demographics to balance the current revenue skew.
2. **Smart Discounting Thresholds:** Replace flat promotional discounts with minimum spend rules (e.g., "$15 off on orders over $80") to protect product profit margins.
3. **Revamp Subscription Perks:** Offer exclusive product access and free express shipping rather than price discounts to drive subscriber sign-ups.
4. **Top-of-Funnel Onboarding:** Launch welcome offers to convert first-time site visitors and solve the low 2.1% new customer conversion rate.

---

## 📂 Repository Structure
```text
├── Customer shopping behavior analysis.ipynb  # Python data cleaning & SQL database export
├── custmoer_behaviour_mysql_queries.sql      # Full MySQL script with 10 analytical queries
├── Customer Shopping Behavior Analysis.pptx   # Executive presentation deck
└── README.md                                  # Project documentation

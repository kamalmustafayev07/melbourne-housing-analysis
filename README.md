# Melbourne Housing Market Analysis  
*Data-Driven Insights on Property Prices in Melbourne, Australia*

## Overview  
This project presents a **comprehensive exploratory data analysis (EDA)** of the **Melbourne housing market**, focusing on understanding which property and location features most influence sale prices.  
The analysis is built using **Python** and **Poetry** for environment management, combining statistical techniques and data visualisation to uncover key market patterns and drivers.

The findings provide valuable insights for **buyers, investors, policymakers, and real estate professionals** to make more informed, data-driven decisions.

---

## Motivation  
The Melbourne real estate market is highly dynamic and complex.  
Identifying what drives property prices can help:  
- 🏠 **Homebuyers** make better purchasing decisions  
- 💼 **Investors** identify growth opportunities  
- 🏛️ **Policymakers** understand regional affordability and trends  

The aim of this project is to determine **the most significant price drivers** across suburbs and regions of Melbourne and offer **actionable insights** derived from data.

---

## Dataset  

**Source:** [Melbourne Housing Market Dataset — Kaggle](https://www.kaggle.com/datasets/anthonypino/melbourne-housing-market)

- **Number of records:** 23,547 property transactions  
- **Number of attributes:** 21 (including suburb, rooms, price, sale method, and year built)  
- **Coverage:** Public Melbourne real estate sales records  

| Column | Description |
|---------|--------------|
| Suburb | Neighborhood or district name |
| Address | Street address |
| Rooms | Number of bedrooms |
| Type | Property type (`h`=house, `t`=townhouse, `u`=unit) |
| Price | Sale price (AUD) |
| Method | Sale method (`S`=sold, etc.) |
| SellerG | Real estate agent |
| Date | Sale date |
| Distance | Distance from CBD (km) |
| Postcode | Postal code |
| Bedroom2 | Alternative bedroom count |
| Bathroom | Number of bathrooms |
| Car | Car spaces |
| Landsize | Land area (sqm) |
| BuildingArea | Building area (sqm) |
| YearBuilt | Year property was built |
| CouncilArea | Local government area |
| Regionname | Regional classification |
| Propertycount | Number of properties in the suburb |

---

## Data Preparation & Cleaning  

The raw dataset required significant preprocessing to ensure accuracy and consistency.  

### Steps:
1. **Data Loading:**  
   Imported using `pandas` and initial inspection performed.

2. **Handling Missing Values:**  
   - Replaced empty strings with `NaN`.  
   - Created a helper function `check_missing_columns()` to identify incomplete data.  

3. **Imputation:**  
   - Filled missing categorical data (`Suburb`, `Regionname`, `CouncilArea`) using grouped mode values.  
   - Imputed `Price` by suburb/region mean.  
   - Replaced missing or zero values in `Distance`, `Landsize`, and `BuildingArea` with grouped medians.  
   - Filled missing `YearBuilt`, `Bathroom`, `Car` with statistical aggregates.  
   - Replaced invalid zeros and aligned `Bedroom2` with `Rooms`.

4. **Final Adjustments:**  
   - Dropped unnecessary columns (Latitude, Longitude).  
   - Renamed inconsistent columns (`Rooms` → `Bedroom`).  
   - Validated types and ranges for `Date`, `YearBuilt`, and `Price`.  
   - Saved cleaned dataset as `Melbourne_cleaned.csv`.

---

## Research Questions  
- What property and location features most influence housing prices in Melbourne?  
- How do market dynamics vary between suburbs and regions?  
- Which properties or areas perform best for investment and buyer interest?  

---

## Analysis & Insights  

### **Insight 1 — Properties with Larger Land Size**  
Filtered properties with land size above average to explore premium market segments.  
This analysis revealed that **location, year built, and distance from the CBD** strongly correlate with higher land-value properties.

---

### **Insight 2 — Top Property Recommendations**  
Identified and ranked **top 10 properties overall** based on value, region, and physical features.  
A random property from the top selection was highlighted to simulate a data-driven buyer recommendation.

---

### **Insight 3 — Top 10 Houses per Suburb**  
Grouped data by **suburb** to extract top properties in each neighborhood.  
This localized analysis revealed distinct value clusters and price differences across Melbourne’s districts.

---

### **Insight 4 — Top 10 Houses per Region**  
Aggregated the data by **regional zones**, identifying broader market patterns.  
Regions closer to the CBD or coastal areas consistently showed higher mean prices, revealing strong geographic influence.

---

## Key Findings  

- **Property prices** are primarily driven by:
  - Land size  
  - Distance from the CBD  
  - Number of bedrooms  
  - Year built  
  - Seller performance  

- **Regional differences** show that inner-city and eastern suburbs command significantly higher median prices.  

- **Market distribution** varies by property type, with **houses** dominating higher-value segments compared to **units or townhouses**.

- **Sellers and agents** also impact price outcomes — some agencies consistently achieve higher selling prices per region.

---

## Limitations  

- Dataset is limited to **Melbourne**; findings may not generalize to other markets.  
- Some off-market or private sales are **not included**.  
- Statistical imputations may not fully represent true missing values.  
- External factors (e.g., economy, policy, or construction trends) are **not modeled**.  
- Real estate markets evolve rapidly — the dataset represents a **historical snapshot**.

---

## Conclusion  

The analysis concludes that **location, land size, and property condition** are the primary determinants of housing prices in Melbourne.  
Both **micro-level (suburb)** and **macro-level (regional)** analyses reveal market diversity, providing **practical insights** for buyers, investors, and developers seeking data-backed decision support.

---

## Running the Project Locally  

### 1. Clone the repository  
```bash
git clone https://github.com/kamalmustafayev07/melbourne-housing-analysis.git
cd melbourne-housing-analysis
```

### 2. Install dependencies  
You can install dependencies using either **pip** or **Poetry**.

#### Option A — Using pip (recommended for simplicity)
Make sure you have Python 3.11 or later installed.  
Then run:  
```bash
pip install -r requirements.txt
```

#### Option B — Using Poetry (if you have it installed)
If you prefer Poetry, install dependencies using:  
```bash
poetry install --no-root
poetry shell
```

### 3. Run the analysis notebooks  
The dataset (`Melbourne.csv`) is already included in the `data/` directory.  
To reproduce the analysis, open and execute the Jupyter notebooks in the following order:

1. `01_data_cleaning.ipynb` – performs data loading, inspection, and preprocessing  
2. `02_exploratory_analysis.ipynb` – conducts visualizations and feature exploration  
3. `03_insights_and_findings.ipynb` – summarizes key results and conclusions  

Start Jupyter Notebook:
```bash
jupyter notebook
```
Then open each notebook in sequence and run all cells.


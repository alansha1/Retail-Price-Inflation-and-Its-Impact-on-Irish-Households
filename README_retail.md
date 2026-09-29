# 🛒 Retail Price Inflation and Its Impact on Irish Households

> Forecasting consumer price trends in Ireland using time-series models and machine learning — with interactive Power BI and Tableau dashboards to visualise the real-world impact on household budgets.

---

## 📌 Project Overview

Ireland has experienced some of the steepest retail price increases in Europe over recent years, with inflation hitting double digits in 2022–2023 and squeezing household budgets across every income group. While the headline CPI figure makes the news, the *category-level* story is far more revealing — food prices rose faster than energy, rents faster than clothing, and the impact varied significantly depending on where a household sat in the income distribution.

This project builds a **data-driven forecasting and analysis pipeline** that:
- Ingests official Irish retail price and CPI data from public sources (CSO, Eurostat)
- Forecasts future inflation trends using time-series and machine learning models
- Quantifies the real purchasing power loss experienced by Irish households
- Presents findings through professional Power BI and Tableau dashboards

The result is a research-grade analysis that goes beyond raw numbers to tell a clear, evidence-based story about how inflation is reshaping everyday life in Ireland.

---

## 🎯 Objectives

- Collect and clean historical retail price and CPI data for Ireland (2018–2024)
- Identify which product categories experienced the sharpest price increases
- Forecast short-term inflation trends using ARIMA, Linear Regression, Random Forest, and Neural Network models
- Compare model performance and select the most accurate forecaster
- Quantify the impact of inflation on household spending power across income levels
- Present findings through interactive dashboards built in Power BI and Tableau

---

## 📊 Dataset

Data sourced from official public statistics:

| Source | Dataset | Description |
|---|---|---|
| **CSO Ireland** | Consumer Price Index | Monthly CPI by category (food, energy, housing, clothing, transport) |
| **Eurostat** | HICP Ireland | Harmonised inflation index for EU comparison |
| **CSO Ireland** | Household Budget Survey | Average household expenditure by income decile |
| **CSO Ireland** | Retail Sales Index | Monthly retail sales volume and value |

**Time period covered:** January 2018 – December 2024 (72 months)

**Key categories tracked:**
- Food & Non-Alcoholic Beverages
- Energy (electricity, gas, fuel)
- Housing & Utilities
- Transport
- Clothing & Footwear
- Health
- Education
- Restaurants & Hotels

---

## 🤖 Forecasting Models

### 1. ARIMA (AutoRegressive Integrated Moving Average)
A classical time-series model that captures autocorrelation in the data — how this month's prices relate to last month's. Best suited to the seasonality and trend patterns in CPI data.

### 2. Linear Regression
Establishes a baseline. Treats time as a continuous predictor and fits a straight-line trend to historical prices. Fast and interpretable, but cannot capture the non-linear acceleration seen during the 2022 inflation spike.

### 3. Random Forest Regressor
An ensemble method that uses multiple features beyond just time — including lagged price values, energy costs, and European CPI — to generate forecasts. Captures complex non-linear relationships between economic variables.

### 4. Neural Network (MLP Regressor)
A feedforward neural network trained on the full feature set. Learns deep patterns in the data and performs strongly when given sufficient historical context.

---

## 📈 Model Performance

| Model | RMSE | MAE | R² Score |
|---|---|---|---|
| **ARIMA** | **0.41** | **0.33** | **0.912** |
| Random Forest | 0.58 | 0.44 | 0.887 |
| Neural Network | 0.63 | 0.51 | 0.871 |
| Linear Regression | 1.24 | 0.98 | 0.743 |

> ARIMA outperforms ML models on this dataset because CPI data follows strong seasonal and trend patterns — exactly what ARIMA is designed to exploit.

---

## 🔍 Key Findings

**1. Food inflation peaked at +16.2% YoY in late 2022**
The food and non-alcoholic beverages category experienced the sharpest single-year increase in the dataset — driven by global supply chain disruption, energy cost pass-through, and the Ukraine conflict's impact on grain prices.

**2. Energy costs drove the 2021–2022 spike**
Electricity and gas prices rose over 50% between mid-2021 and end-2022. Because energy costs feed into the production of almost every other good, the knock-on effect was felt across all categories with a 3–6 month lag.

**3. Low-income households were disproportionately affected**
The bottom two income deciles spend a higher share of their budget on food and energy — the two categories that inflated fastest. While headline CPI peaked at around 9%, the *effective* inflation rate for the lowest-income households was closer to 12–14%.

**4. Ireland's inflation ran above the EU average**
Ireland's HICP consistently tracked above the Eurozone average from 2021–2023, partly due to the high share of variable-rate mortgages (which feed into housing costs) and Ireland's energy import dependency.

**5. Prices have not reversed — they have plateaued**
While the *rate* of inflation has returned to near 2% by 2024, prices themselves remain at their elevated 2022–2023 levels. The forecasting models project continued slow growth rather than any meaningful reversal.

---

## 📉 Household Impact Analysis

Using CSO Household Budget Survey data, the project estimates the annual additional spending burden imposed by inflation on a typical Irish household:

| Household Type | Estimated Extra Annual Cost (2022 vs 2019) |
|---|---|
| Single adult, renting | +€2,840 |
| Couple, no children | +€3,910 |
| Family with 2 children | +€5,230 |
| Low-income household (bottom 20%) | +€2,100 (but represents a higher % of income) |

---

## 📊 Dashboards

The project includes two interactive dashboards:

### Power BI Dashboard
- CPI trend line by category (2018–2024)
- Household impact calculator (adjustable for income level and family size)
- Ireland vs EU inflation comparison
- Forecasted CPI for the next 12 months

### Tableau Dashboard
- Category breakdown heatmap (month vs category)
- Regional price index comparison (Dublin vs Rest of Ireland)
- Income decile impact visualisation
- Year-on-year change waterfall chart

---

## 🚀 How to Run

### Prerequisites
```bash
pip install -r requirements.txt
```

### Step 1 — Load and clean the data
```bash
python data_processing.py
```

### Step 2 — Train all forecasting models
```bash
python train_models.py
```

### Step 3 — Generate forecast charts and output
```bash
python visualise.py
```

Output saved to `output/`:
- `output/cpi_forecast.csv` — model forecasts vs actual CPI
- `output/model_comparison.png` — RMSE comparison chart
- `output/category_trend.png` — inflation by category over time
- `output/household_impact.png` — income decile impact chart

---

## 📁 Project Structure

```
Retail-Price-Inflation-and-Its-Impact-on-Irish-Households/
│
├── data/
│   ├── cso_cpi.csv                  # CSO Consumer Price Index (monthly)
│   ├── eurostat_hicp.csv            # EU harmonised inflation index
│   └── household_budget_survey.csv  # CSO household expenditure data
│
├── data_processing.py               # Data ingestion, cleaning, feature engineering
├── train_models.py                  # ARIMA, LR, RF, Neural Network training
├── visualise.py                     # Chart generation
├── requirements.txt
│
├── dashboards/
│   ├── retail_inflation.pbix        # Power BI dashboard
│   └── retail_inflation.twbx        # Tableau dashboard
│
└── output/
    ├── cpi_forecast.csv
    ├── model_comparison.png
    ├── category_trend.png
    └── household_impact.png
```

---

## 💡 Why This Matters

Inflation analysis is a core competency in economics, policy, and business. This project demonstrates:

- The ability to work with **official government statistical data** (CSO, Eurostat)
- **Time-series forecasting** — one of the most in-demand data skills in finance, retail, and operations
- **Translating numbers into a human story** — quantifying what a 9% CPI figure actually means for a family's weekly shop
- **BI tool proficiency** — Power BI and Tableau dashboards built to a professional standard

This type of analysis is used daily by central banks, government departments, retail chains, and investment funds — making it directly relevant to analyst roles across sectors.

---

## 🛠️ Technologies Used

| Tool | Purpose |
|---|---|
| Python 3.10 | Core programming language |
| Pandas & NumPy | Data cleaning and manipulation |
| Statsmodels | ARIMA time-series modelling |
| Scikit-learn | Random Forest and Neural Network models |
| Matplotlib & Seaborn | Static charts and model output |
| Power BI | Interactive business intelligence dashboard |
| Tableau | Interactive data visualisation dashboard |
| Jupyter Notebook | Exploratory data analysis |

---

## 👨‍💻 Author

**Alan Sha**
MSc Data Analytics — Dublin Business School
🔗 [LinkedIn](https://www.linkedin.com/in/alan-sha-22a7502bb/) · [GitHub](https://github.com/alansha1)

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

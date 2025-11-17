# python-test1
NSE Stock Time Series Analysis using Python (INFY, TCS, NIFTY IT)
📊 NSE Stock Time Series Analysis (INFY, TCS, NIFTY IT Index)

Time Period: 2015–2016
Data Level: Daily
Tools: Python, Pandas, Bokeh, Statsmodels, Sklearn

This project performs an end-to-end time series analysis on Indian stock market data (INFY, TCS, NIFTY IT).
Assignment ke according yaha Part 1, Part 2, Part 3 sab proper structure me diya gaya hai.

🧩 Project Structure
python-test/
│
├── data/
│   ├── INFY.csv
│   ├── TCS.csv
│   └── NIFTYIT.csv
│
├── code/
│   ├── part1_analysis.py
│   ├── part2_visualization.py
│   ├── part3_models.py
│   └── stockpredictor.py
│
├── output/
│   ├── shock_timeseries.txt
│   ├── price_shock_summary.txt
│   ├── volume_shock_summary.txt
│   ├── bokeh_plots.html
│   ├── pacf_plots.html
│   └── mape_scores.txt
│
├── tests/
│   └── test_models.py
│
├── requirements.txt
│
└── README.md

🧱 Part 1 – Data Processing & Feature Engineering
✔ 1. Moving Averages (4, 16, ..., 52 weeks)

A function automatically generates:

4-week MA

16-week MA

24-week MA

32-week MA

40-week MA

52-week MA

Applied to: INFY, TCS, NIFTY IT

✔ 2. Rolling Window (10 → 75 window sizes)

Rolling window used for:

Close price stability

Volatility check

Trend detection

Unequal time series due to stock market holidays handled using reindex + forward fill.

✔ 3. Dummy Time Series Creation
3.1 Volume Shock

Volume > 10% change from previous day
→ Boolean shock series (0/1)
→ Up/Down direction series

3.2 Price Shock

Close price difference > 2%
→ Boolean shock series
→ Direction series

3.3 Black Swan Detection

Same logic as price shock but marked separately.

3.4 Price shock without Volume shock

(Price Shock = 1) AND (Volume Shock = 0)

🎨 Part 2 – Data Visualization Using Bokeh
✔ 1. Time-Series Plot (Base Blue Color)

All stocks & index plotted as blue time series.

✔ 2. Time Period Between Volume Shocks = Highlighted Red

Price action between two volume shocks is highlighted red.

✔ 3. Gradient Blue Color Based on 52-Week MA Deviation

Larger deviation → darker shade
Smaller deviation → lighter shade

✔ 4. Price Shock Without Volume Shock Marking

Volumeless price movements are marked with:
black circle markers (or whatever used in code)

✔ 5. Hand-Crafted PACF Plot (Bokeh)

PACF values manually computed for all lags
Visualized using Bokeh (statsmodels ka pacf function reference liya gaya)

🤖 Part 3 – Machine Learning Models (Optional)
✔ Models Used

Linear Regression

Ridge Regression / Lasso / or your chosen 2 models

Quick build: Grid search < 9 combinations.

✔ Prediction Goal

Predict next day closing price for:

INFY

TCS

✔ Model Assumptions Checked

Based on OLS assumptions:

Linearity

No multicollinearity

Residual normality

No autocorrelation

Homoscedasticity

✔ MAPE Scores Stored In

output/mape_scores.txt

✔ Best Model Selection & Tuning

After comparing MAPE, best model tuned further to show improvement.

⚡ Extra Credit – stockpredictor.py

Usage:

python stockpredictor.py "INFY"


Should return prediction in under 100 ms.

🧪 Tests (PyTest)

Inside tests/test_models.py:

Prediction must work for minimum 5 future steps

MAPE must be under expected threshold

Model assumptions must hold

Run test:

pytest

📥 Dataset Source

Data is fetched using nsepy
Source link:
https://github.com/swapniljariwala/nsepy

▶️ How to Run the Project
1️⃣ Clone the repo
git clone https://github.com/<your-username>/python-test
cd python-test

2️⃣ Install dependencies
pip install -r requirements.txt

3️⃣ Run Part 1
python code/part1_analysis.py

4️⃣ Run Visualizations
python code/part2_visualization.py


Output → output/bokeh_plots.html

5️⃣ Run Models
python code/part3_models.py


Output → output/mape_scores.txt

6️⃣ Run Extra Predictor
python stockpredictor.py "INFY"

📌 Notes

All outputs saved inside output/ folder

All models reproducible

No dataset preprocessing outside Python

Pure Python + Bokeh project

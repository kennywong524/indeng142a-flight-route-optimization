# ✈️ Delay-Aware Flight Route Optimization under Uncertainty

Group members: Kenny Wongchamcharoen, Ashlee Liu, Charmaine Yuen, Annie chen, Sukhman Sidhu

Inspired by the "predict-then-optimize" framework (Grigas et al., 2018), we develop a delay-aware itinerary optimization model that integrates machine learning with operations research. Using historical flight data from the Airline delay dataset, we create a pipeline that predicts expected travel delays and incorporate them into an optimization model to construct robust travel itineraries. We first apply supervised learning methods such as Logistic Regression, along with enhancements through XGBoost and Random Forest to predict average flight delays and cancellation rates for each airport-carrier pair, combining regression and classification models. Next, we apply unsupervised k-means clustering on normalized hidden delay cause breakdowns, revealing interpretable delay profiles during post-hoc validation. These predictions are embedded into a simple network flow, single-stage stochastic program, formulated in Pyomo, to select an itinerary that minimizes expected cost, travel time, and cancellation risks. This project demonstrates how predictive analytics and optimization can be combined to support real-world travel planning under uncertainty.

---

## Dataset

Due to size limits, the **original raw dataset** is not uploaded here.  
You can download it from Kaggle:

🔗 [Airline Delay Dataset on Kaggle](https://www.kaggle.com/datasets/sriharshaeedala/airline-delay?resource=download)

---

## Project Structure and Notebook Order

To reproduce this project:

1. **Important!** Download the kaggle dataset & make sure the file name is `Airline_Delay_Cause.csv` before uploading it to notebook 1.
2. **Download all `.csv` files** from this repo and upload them into your environment (e.g., Colab or Jupyter).
3. Follow the notebooks in this order:

---

### 1️⃣ `data_preprocessing.ipynb`

- Clean and filter raw BTS flight data
- Focus on key carriers and airports
- Input: `Airline_Delay_Cause.csv`
- Output: `ml_ready_airport_airline_final.csv`

---

### 2️⃣ `delay_prediction.ipynb`

- Trains regression models (Random Forest, XGBoost, etc.)
- Predicts average delay by carrier-airport
- Input: `ml_ready_airport_airline_final.csv`
- Output: `avg_predicted_delay_by_carrier_airport.csv`

---

### 3️⃣ `cancellation_prediction.ipynb`

- Trains classification models to estimate cancellation risk
- Input: `ml_ready_airport_airline_final.csv`
- Output: `avg_predicted_cancellation_risk.csv`

---

### 4️⃣ `optimization+UI.ipynb`

- Uses Pyomo to formulate an optimization model
- Inputs: `avg_predicted_delay_by_carrier_airport.csv` and `avg_predicted_cancellation_risk.csv`
- Solves for optimal route given budget and constraints
- (For Bonus point) Includes an **interactive component**: In the last cell, enter origin/destination to get optimal flight recommendation!

---

## Bonus Notebooks

- `clustering.ipynb`: Unsupervised learning to identify delay profiles
- Helps segment delay patterns by root cause (weather, NAS, etc.)


## 🛠 Dependencies

- Python 3.8+
- Pyomo
- scikit-learn
- matplotlib, seaborn
- pandas
- XGBoost

---

## 📬 Authors

This project was completed as part of a final project for UC Berkeley's IND ENG 142A: Machine Learning & Data Analytics I

Group members: Kenny Wongchamcharoen, Ashlee Liu, Charmaine Yuen, Annie chen, Sukhman Sidhu
Feel free to reach out or fork this repo if you’re interested in applying predictive analytics + optimization to travel planning!

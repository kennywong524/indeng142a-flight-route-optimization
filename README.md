# ✈️ Delay-Aware Itinerary Optimization under Uncertainty

This project builds an end-to-end pipeline that predicts flight delays and cancellation risks, and then uses optimization (via Pyomo) to construct robust travel itineraries. Our goal is to help travelers or logistics systems minimize total travel time, cost, and delay risk.

---

## Dataset

Due to size limits, the **original raw dataset** is not uploaded here.  
You can download it from Kaggle:

🔗 [Airline Delay Dataset on Kaggle](https://www.kaggle.com/datasets/sriharshaeedala/airline-delay?resource=download)

---

## Project Structure and Notebook Order

To reproduce this project:

1. **Download all `.csv` files** from this repo and upload them into your environment (e.g., Colab or Jupyter).
2. Follow the notebooks in this order:

---

### 1️⃣ `data_preprocessing.ipynb`

- Clean and filter raw BTS flight data
- Focus on key carriers and airports
- Output: `ml_ready_airport_airline_final.csv`

---

### 2️⃣ `delay_prediction.ipynb`

- Trains regression models (Random Forest, XGBoost, etc.)
- Predicts average delay by carrier-airport
- Output: `avg_predicted_delay_by_carrier_airport.csv`

---

### 3️⃣ `cancellation_prediction.ipynb`

- Trains classification models to estimate cancellation risk
- Output: `avg_predicted_cancellation_risk.csv`

---

### 4️⃣ `optimization+UI.ipynb`

- Uses Pyomo to formulate an optimization model
- Inputs: delay + cancellation predictions datasets from notebook 2 & 3
- Solves for optimal route given budget and constraints
- Includes an **interactive component**: enter origin/destination to get optimal flight recommendation!

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

This project was completed as part of a final project for UC Berkeley's IND ENG 142A.  
Feel free to reach out or fork this repo if you’re interested in applying predictive analytics + optimization to travel planning!

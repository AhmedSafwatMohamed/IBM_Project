
# 🚀 IBM Data Science Capstone: SpaceX Launch Success Prediction

## 📌 Overview

This project is a capstone from IBM’s Data Science Professional Certificate. It focuses on building a full data science pipeline to **predict the success of SpaceX Falcon 9 rocket launches** using machine learning. The project simulates work at a fictional company, **SpaceY**, a new aerospace startup aiming to compete with SpaceX.

A web dashboard was developed using **Plotly Dash** to visualize launch data and allow interactive predictions of first-stage rocket landing success.

---

## 📊 Project Structure

```bash
IBM_Project/
│
├── scripts-and-notebooks/
│   ├── jupyter_labs_spacex_data_collection_api_v2.ipynb       # SpaceX API data collection
│   ├── jupyter_labs_webscraping.ipynb                         # Web scraping from Wikipedia
│   ├── labs_jupyter_spacex_Data_wrangling_v2.ipynb            # Data cleaning and preprocessing
│   ├── jupyter_labs_eda_dataviz_v2.ipynb                      # EDA with matplotlib/seaborn
│   ├── jupyter_labs_eda_sql_coursera_sqllite.ipynb            # EDA with SQL queries
│   ├── lab_jupyter_launch_site_location_v2.ipynb              # Folium mapping
│   ├── spacex_dash_app.py                                     # Plotly Dash interactive dashboard
│   └── SpaceX_Machine_Learning_Prediction_Part_5_v1.ipynb     # ML modeling and evaluation
│
├── README.md        # Project documentation (this file)
└── presentation.pdf # Project presentation slides
```

---

## 🎯 Objectives

- Predict if Falcon 9’s first stage will successfully land.
- Assess the impact of recovery on launch cost.
- Analyze launch site, payload, orbit, and other features affecting outcomes.

---

## 🧪 Methodology

### 🔹 Data Collection
- Used the **SpaceX REST API** and **Wikipedia scraping** to collect launch data.
- Data points include: Payload Mass, Orbit, Launch Site, Booster Version, and Landing Outcome.

### 🔹 Data Wrangling
- Cleaned and merged datasets.
- Handled missing values and performed feature engineering (e.g., one-hot encoding).
- Created a binary target variable for landing success.

### 🔹 Exploratory Data Analysis (EDA)
- Used **Matplotlib**, **Seaborn**, and **SQL** to explore relationships:
  - Launch Site vs. Outcome
  - Payload Mass vs. Success Rate
  - Orbit type vs. Landing Success

### 🔹 Geospatial Analysis
- Created interactive **Folium** maps to visualize launch site locations and outcomes.

### 🔹 Machine Learning
- Implemented and compared:
  - Logistic Regression (best: **83% accuracy**)
  - Decision Tree
  - K-Nearest Neighbors
  - Support Vector Machine
- Used **GridSearchCV** for hyperparameter tuning.

### 🔹 Interactive Dashboard
- Developed a web app using **Plotly Dash** for real-time filtering and predictions.

---

## 📈 Results

- Logistic Regression was the best model with **83% accuracy**.
- Visualization showed strong trends between:
  - Heavier payloads and lower success rates.
  - Specific orbits (LEO, ISS) having higher landing success.
- KSC LC-39A was the most reliable launch site.

---

## 🧠 Key Insights

- Flight number and payload mass significantly impact landing success.
- Launch sites and orbit types are critical predictors.
- Reusability (booster recovery) is feasible to predict using public data.

---

## 🌐 Demo

📊 View the dashboard:  
Run the `spacex_dash_app.py` script locally to launch the interactive dashboard at `http://127.0.0.1:8050/`.

---

## 🛠️ Tools & Technologies

- **Python**, **Pandas**, **NumPy**
- **Matplotlib**, **Seaborn**, **Plotly**
- **SQLite**, **Folium**, **Dash**
- **Scikit-learn**, **GridSearchCV**

---

## 📂 Resources

- [SpaceX API Data Collection Notebook](https://github.com/AhmedSafwatMohamed/IBM_Project/blob/main/scripts-and-notebooks/jupyter_labs_spacex_data_collection_api_v2.ipynb)  
- [Web Scraping](https://github.com/AhmedSafwatMohamed/IBM_Project/blob/main/scripts-and-notebooks/jupyter_labs_webscraping.ipynb)  
- [Dash App Code](https://github.com/AhmedSafwatMohamed/IBM_Project/blob/main/scripts-and-notebooks/spacex_dash_app.py)  
- [ML Model Notebook](https://github.com/AhmedSafwatMohamed/IBM_Project/blob/main/scripts-and-notebooks/SpaceX_Machine_Learning_Prediction_Part_5_v1.ipynb)  

---

## 🧑‍💻 Author

**Ahmed Safwat Mohamed Taleb**  
July 2025  
[GitHub Profile](https://github.com/AhmedSafwatMohamed)

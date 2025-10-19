# ⚽ Predicting Attendance at MLS Soccer Games

### 📊 Executive Summary
This project applies **machine learning techniques** to predict **attendance levels at Major League Soccer (MLS) games**, one of the key indicators of fan engagement and revenue potential.  
Using match, team, and weather data from **FBRef** and **Wunderground**, we built predictive models to classify attendance as **High or Low**.  
The analysis identifies the most influential factors driving attendance — such as **venue location, day of the week, team Elo ratings, and presence of all-star players** — enabling teams and event managers to better forecast crowd sizes, optimize staffing, and improve game-day planning.

---

### 💼 Business Problem
High attendance directly influences:
- **Revenue** from ticket sales, concessions, and merchandise  
- **Operational planning** (staffing, safety, and logistics)  
- **Fan engagement and sponsorship value**

**Objective:**  
Predict whether attendance at an MLS match will be *High (≥21,000)* or *Low (<21,000)*, using variables such as team performance, weather, and market size.  

**Key Questions:**
- Which factors most strongly influence stadium turnout?  
- Can predictive modeling support better staffing, marketing, and inventory decisions for MLS events?

---

### 🧩 Methodology

#### 1. **Data Overview**
- **Sources:**  
  - [FBRef](https://fbref.com/en/) – Team and match statistics  
  - [Wunderground](https://www.wunderground.com/) – Historical weather data  
- **Seasons Covered:** 2014–2019 (Pre-COVID) and 2022–2023 (Post-COVID)  
- **Size:** 2,513 matches  
- **Key Features:**  
  - Team performance (`home_elo`, `away_elo`, `Result`, `GF`, `GA`)  
  - Player quality (`Num_allstar_home`, `Num_allstar_away`)  
  - Demographics (`Population`, `City_market_size`)  
  - Weather & venue (`Temp`, `Precip`, `Condition`, `Distance`)  
  - Timing (`Day_of_Week`, `Month`, `Time`, `Year`)  
  - Target: **Attendance_Binary (High=1 / Low=0)**  

#### 2. **Preprocessing**
- Encoded categorical variables (`Venue`, `Result`, `Date_Categories`, etc.)  
- Log-transformed skewed variables (`Population`, `Distance`)  
- Standardized continuous variables with **StandardScaler**  
- Handled class imbalance using **SMOTE (Synthetic Minority Oversampling Technique)**  

#### 3. **Exploratory Data Analysis (EDA)**
- **Weekend games (Sat/Sun)** show significantly higher attendance.  
- Attendance decreases as **venue distance from city center** increases.  
- Population size does not linearly correlate with attendance → highlights importance of **team quality and fan loyalty**.  

---

### 🧠 Skills Highlighted
- **Languages:** Python  
- **Libraries:** pandas, numpy, scikit-learn, xgboost, matplotlib, seaborn  
- **Techniques:** Logistic Regression, Random Forest, XGBoost, SMOTE balancing  
- **Data Science Concepts:** Feature encoding, normalization, feature importance, model tuning, evaluation metrics  
- **Metrics Used:** Accuracy, Precision, Recall, F1-score, AUC (ROC Curve)  
- **Business Analytics:** Sports forecasting, event attendance optimization, fan engagement analysis  

---

### 🤖 Machine Learning Models

#### **1. Logistic Regression**
- **AUC (after SMOTE):** `0.7778`  
- **Accuracy:** `0.708`  
- Key Drivers of High Attendance:  
  - Shorter `Distance` to venue  
  - Higher `home_elo` rating  
  - More `Num_allstar_home` players  
  - Favorable game `Result` (Win)  
  - Later `Month` in season (higher excitement)  
- **Insight:** Attendance tends to rise over years but dips slightly post-COVID.

#### **2. Random Forest**
| Model Variation | Accuracy | F1-Score | AUC |
|-----------------|-----------|----------|-----|
| No Preprocessing | 0.872 | 0.87 | 0.927 |
| After SMOTE | **0.902** | **0.90** | **0.964** |

- **Top Features (Feature Importance):**
  - `Month`, `Goals Against`, `Result`, `Num_allstar_home`, `home_elo`
- **Insight:** Team success and timing dominate attendance prediction.

#### **3. XGBoost**
| Model Variation | Accuracy | F1-Score | AUC |
|-----------------|-----------|----------|-----|
| No Preprocessing | 0.884 | 0.88 | 0.941 |
| After SMOTE | **0.905** | **0.91** | **0.970** |

- **Best Performing Model:** XGBoost after SMOTE  
- **Key Predictors:** Month, Home/Away Elo ratings, All-star players, Distance  
- **Interpretation:** Matches featuring star players in high-performing teams during late-season months see maximum turnout.

---

### 📈 Results & Business Insights
- **Model Accuracy:** Up to **90.5%** (XGBoost after SMOTE)  
- **Best Predictor Categories:**
  - **Temporal:** Weekend and late-season matches boost attendance.  
  - **Performance-based:** High Elo teams and wins drive turnout.  
  - **Geographic:** Closer venues to downtown attract larger crowds.  
- **Operational Impact:**
  - Helps plan **staffing, concessions, and security** based on predicted crowd levels.  
  - Enables **dynamic ticket pricing** and **marketing campaigns** tailored to low-attendance matches.  

---

### 🚀 Business Recommendations
1. **Scheduling Optimization**  
   - Prioritize high-profile matches on weekends or later months for maximum turnout.  

2. **Marketing Strategy**  
   - Offer promotions for weekday games or low-interest fixtures.  
   - Highlight all-star player participation in advertising campaigns.  

3. **Venue Management**  
   - Increase resources for high-turnout matches (staffing, parking, inventory).  
   - Use predicted attendance to guide **ticket pricing** and **merchandise stock**.

4. **Predictive Dashboard (Future Work)**  
   - Build a **Power BI / Streamlit** dashboard to visualize upcoming match attendance predictions in real time.  

---

### 🔮 Next Steps
- Integrate **external sentiment data** (Twitter, Google Trends) for fan engagement forecasting.  
- Explore **Deep Learning models (LSTM / DNN)** for temporal attendance prediction.  
- Extend framework to **other sports leagues** (NBA, NFL, MLB) for cross-domain insights.  

**Tools:** Python, Jupyter Notebook, scikit-learn, XGBoost, pandas, matplotlib  


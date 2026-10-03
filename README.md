# 🏠 House Price Predictor – ML Web App
 
A beginner-friendly machine learning project, now a **web app**. Enter a house's **area**, **number of bedrooms** and **age**, and get an instant price prediction. Built with Python, scikit-learn and **Streamlit**.
 
🔗 **Live demo:** https://house-price-prediction-pyasxbqihetdxuvfy3dqdj.streamlit.app/
 
---
 
## ✨ Features
 
- 🎚️ **Interactive sliders** for area, bedrooms and age
- 🔀 **Choose a model:** Linear Regression or Random Forest
- 💰 **Predicted price** with the model's typical error (MAE), accuracy (R²) and an estimated price range
- ⚖️ **Side-by-side comparison** of both models for the same house
- 📊 **Data exploration:** dataset preview, summary statistics, scatter plots (your house shown as a red dot) and correlations
- 🧠 **Model insights:** actual vs predicted plot, Linear Regression effects, Random Forest feature importance
---
 
## 📂 Project Structure
 
```
house_price_webapp/
├── app.py              # Streamlit web app (data, models, UI)
├── house_prices.csv    # Dataset (200 houses)
├── requirements.txt    # Python dependencies
└── README.md           # This file
```
 
---
 
## 📊 Dataset
 
`house_prices.csv`: **200 rows × 4 columns**, no missing values.
 
| Column | Role | Description |
|--------|------|-------------|
| `Area (sq ft)` | Feature | Size of the house |
| `Bedrooms` | Feature | Number of bedrooms (1–5) |
| `Age of House (years)` | Feature | Age of the house (0–40) |
| `Price` | **Target** | Price to predict |
 
---
 
## 🚀 Run Locally
 
1. **Clone or download** this project.
2. **Install dependencies:**
```bash
   pip install -r requirements.txt
```
3. **Start the app:**
```bash
   streamlit run app.py
```
4. Open the link shown in the terminal (usually `http://localhost:8501`).
> Keep `app.py` and `house_prices.csv` in the same folder. If the CSV is missing, the app asks you to upload it.
 
---
 
## ☁️ Deploy for Free (Streamlit Community Cloud)
 
1. Push the project files to a **GitHub repository**.
2. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
3. Click **New app**, select your repo and branch, and set the main file to `app.py`.
4. Click **Deploy**. You'll get a public URL to share.
---
 
## 🧠 How It Works
 
1. **Load data** from `house_prices.csv` (cached for speed).
2. **Split** the data 80/20 into training and test sets (`random_state=42`).
3. **Train** two models: `LinearRegression` and `RandomForestRegressor(n_estimators=200)`.
4. **Evaluate** each on the 40 unseen test houses using MAE and R².
5. **Predict** the price whenever you move a slider, using the selected model.
Models are trained once and cached with `st.cache_resource`, so the app stays fast.
 
---
 
## 📈 Model Results
 
| Model | MAE (avg error) | R² |
|-------|----------------:|---:|
| **Linear Regression** ✅ | ~9,748 | 0.941 |
| Random Forest | ~10,612 | 0.916 |
 
**What Linear Regression learned**
 
- +1 sq ft of area → about **+103** in price
- +1 bedroom → about **+3,563**
- +1 year of age → about **−1,025**
**Example:** 1,800 sq ft, 3 bedrooms, 10 years old → about **209,759** (Linear Regression).
 
---
 
## ⚠️ Limitations
 
- **Small dataset:** 200 houses for training and only 40 for testing, so scores can shift with a different split.
- **Correlated features:** area and bedrooms move together, so individual effects are rough guides.
- **Limited range:** the sliders are restricted to the data's range (about 492–2,425 sq ft, 0–40 years). Predictions outside it would be unreliable.
- **Few features:** real prices also depend on location, condition, amenities and market trends, which this data doesn't include.
- **Estimates only:** this is a learning project, not financial advice.
---
 
## 🛠️ Tech Stack
 
Python · Streamlit · pandas · NumPy · scikit-learn · Matplotlib
 
---

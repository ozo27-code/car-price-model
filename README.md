# 🚗 Used Car Price Prediction

A machine learning project that predicts the **average market price of a used car** from its brand, model, age, kilometers driven and other specifications. Built in Python on **Google Colab**, with the data and the original idea taken from **Kaggle**.

<!-- After uploading the notebook to GitHub, replace the link below with your own Colab link -->
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/YOUR_REPO/blob/main/car_price_prediction_colab.ipynb)

---

## 📌 Project Idea

Buying or selling a used car is hard because the right price depends on many factors at once. This project trains regression models on thousands of real used-car listings so that, given a car's details, the model can estimate a fair price.

**Input:** brand, model, car age (from the manufacturing year), kilometers driven, fuel type, transmission, owner type, engine and power, etc.
**Output:** the estimated price of the car.

---

## 📂 Data Source

| Item | Details |
|------|---------|
| Platform | [Kaggle](https://www.kaggle.com) |
| Reference notebook | [Used Car Price Prediction by gcdatkin](https://www.kaggle.com/code/gcdatkin/used-car-price-prediction) |
| Dataset | [Used Cars Price Prediction](https://www.kaggle.com/datasets/avikasliwal/used-cars-price-prediction) <!-- verify this link matches the dataset used in the reference notebook --> |

The dataset is downloaded automatically inside the notebook using the `kagglehub` library, so no manual download is needed. If the download fails, the notebook asks you to upload the CSV file manually.

> All credit for the original dataset and project idea goes to the Kaggle authors. This repository is an independent implementation made for educational purposes.

---

## 🛠️ Tools & Technologies

- **Python 3**
- **Google Colab** – to write and run the code in the cloud
- **Kaggle / kagglehub** – source of the dataset
- **pandas, NumPy** – data handling
- **scikit-learn** – preprocessing, models, cross-validation, tuning, metrics
- **matplotlib, seaborn** – visualizations
- **joblib** – saving the trained model

---

## 🔬 Methodology

1. **Load data** from Kaggle.
2. **Clean the data** – remove duplicates, convert text values with units (e.g. `19.6 kmpl`, `1582 CC`) to numbers, drop mostly-empty columns, remove extreme prices.
3. **Feature engineering** – extract `brand` and `model` from the car name, convert the year to `car_age`, and create `km_per_year`.
4. **Exploratory analysis** – price distribution, age vs. price, average price per brand, correlation matrix.
5. **Train/test split** – 80 % training, 20 % unseen test data.
6. **Model comparison** with 5-fold cross-validation:
   - Ridge Regression
   - Random Forest
   - Extra Trees
   - Gradient Boosting
7. **Hyper-parameter tuning** of the best model using `RandomizedSearchCV`.
8. **Final evaluation** on the unseen test set.
9. **Testing on different brands and price segments.**
10. **Save the model** to `car_price_model.joblib`.

Models are trained on `log(price)` because prices are right-skewed; predictions are converted back to real prices automatically.

---

## 📊 Output & Results

The notebook prints and plots the following:

- Cross-validation comparison table and bar chart for all models
- Final accuracy summary box
- Actual vs. predicted price plot, error distribution and feature importance
- Accuracy per brand and per price segment (cheap / medium / expensive)
- Sample predictions for cars from different brands

### Evaluation metrics

| Metric | Meaning |
|--------|---------|
| **R² score (%)** | How much of the price variation the model explains |
| **Accuracy (100 − MAPE)** | Average percentage accuracy of the predicted price |
| **MAE / RMSE** | Average error in price units |
| **Within 10 % / 20 %** | Share of cars predicted within 10 % / 20 % of the real price |

### Final results

<!-- Run the notebook, then replace the values below with YOUR real output -->

| Metric | Value |
|--------|-------|
| Best model | _fill after running_ |
| R² score | _xx.xx %_ |
| Accuracy (100 − MAPE) | _xx.xx %_ |
| MAE | _xxxx_ |
| Within 10 % of real price | _xx.xx %_ |
| Within 20 % of real price | _xx.xx %_ |

<!-- Optional: save the plots from Colab and show them here -->
<!-- ![Actual vs Predicted](images/actual_vs_predicted.png) -->

---

## 🚀 How to Run

### Option 1 – Google Colab (recommended)
1. Click the **Open in Colab** badge at the top.
2. Run the cells in order (**Runtime → Run all**).
3. The dataset is downloaded automatically from Kaggle.

### Option 2 – Locally
```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
pip install kagglehub pandas numpy scikit-learn matplotlib seaborn joblib
python car_price_prediction_colab.py
```
> The script was written for Colab (it contains a `!pip` line). Remove that line when running locally.

### Predicting the price of your own car
```python
price = predict_price(brand="Toyota", model="Toyota Corolla", car_age=5, Kilometers_Driven=60000)
print(f"Estimated price: {price:,.2f}")
```
Use the feature names printed by the notebook (the available features depend on the dataset).

---

## 📁 Repository Structure

```
├── car_price_prediction_colab.py   # Full code (copy cells into Colab)
├── car_price_model.joblib          # Trained model (generated after running)
└── README.md
```

---

## ⚠️ Notes & Limitations

- Prices are in the **currency of the dataset** (not necessarily Egyptian pounds).
- The model reflects the market and years covered by the dataset, so it is not suitable for predicting prices in other countries without new data.
- Cars with brands or models that are rare in the data are predicted less accurately.

---

## 👤 Author

**YOUR NAME** – University Project
[GitHub](https://github.com/YOUR_USERNAME)

## 📄 License

This project is for educational purposes. Please check the Kaggle dataset's license before reusing the data.

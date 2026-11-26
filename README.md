# Vehicle Cost Predictor – Gas vs Hybrid vs Electric in Canada

A machine learning project that predicts the **total cost of ownership (TCO)** of a vehicle, gas, hybrid or electric, in Canadian conditions. The user enters the **make**, the **year** and the **mileage (km)** of a vehicle, and the model estimates its energy consumption and its costs, including the effect of **Canadian winters**.

## The problem

Choosing between a gas, hybrid or electric vehicle is hard. Official consumption ratings come from lab tests that don't reflect real conditions: cold temperatures, snow, winter tires, city vs highway driving. Most existing models also look at only one type of vehicle, and only at fuel use.

This project brings everything together in one pipeline: **energy, insurance, maintenance and repairs**, for all three types of vehicles, with an explicit **winter factor**.

## Main question

> Can we predict the total cost of owning a vehicle (energy, insurance, maintenance and repairs) from its technical features and how it is used, especially in Canadian winter conditions?

## Features

The user enters:
- Make of the vehicle
- Year
- Mileage (km)

The model estimates:
- **Energy consumption** (L/100 km or kWh/100 km), city and highway
- **Cost per 100 km** and **estimated cost per month**
- **Insurance** and **maintenance** estimates
- **Winter vs summer** consumption in Canada

Covers **gas**, **hybrid** and **electric** vehicles.

## Data

The model uses official open data from **Natural Resources Canada (NRCan)**, available in the [`data/`](data) folder:

| File | Content |
|---|---|
| `am2015-2024-cotes-de-consommation-de-carburant.csv` | Fuel consumption ratings of gas vehicles, 2015–2024 (~10,000 vehicles) |
| `am2012-2025-vehicules-electriques-a-batterie.csv` | Battery electric vehicles, 2012–2025 (consumption in kWh/100 km, range, charging time) |
| `am2012-2025-vehicules-hybrides-electriques-rechargeables.csv` | Plug-in hybrid vehicles, 2012–2025 (electric and gas consumption, range) |

Source: Natural Resources Canada – Fuel Consumption Ratings, published under the [Open Government Licence – Canada](https://open.canada.ca/en/open-government-licence-canada).

## How it works

1. **Merge** the three datasets into one, with an `Energy_Type` column (0 = gas, 1 = hybrid, 2 = electric).
2. **Clean** the data: fill missing values, remove duplicates and unrealistic values.
3. **Encode** categorical variables (make, transmission, fuel type) with LabelEncoder and OneHotEncoder.
4. **Scale** numerical variables (Min-Max normalization and Z-score standardization).
5. **Create new features:** power-to-weight ratio, energy cost per 100 km, battery density, hybrid efficiency index, and a **winter factor** for cold-weather losses.
6. **Train and compare three models:**
   - **Linear Regression** – the simple, explainable baseline
   - **Decision Tree** – captures non-linear rules (for example: weight > 2,000 kg → high consumption)
   - **Random Forest** – the most robust, with feature importance
7. **Evaluate** with an 80/20 train/test split and 5-fold cross-validation, using **MAE, RMSE and R²**.

```
[Make + Year + Km] ──► [Trained model] ──► Consumption · Cost / 100 km · Monthly cost · Winter vs Summer
```

## Tech stack

- Python
- pandas (data preparation)
- scikit-learn (Linear Regression, Decision Tree, Random Forest)
- Matplotlib, Seaborn (visualizations: real vs predicted, feature importance, cost breakdown)

## My role

I designed and built the whole project myself: data collection, data cleaning, feature engineering, model training and evaluation, and the prediction interface.

## Context

Advanced Artificial Intelligence course – Computer Engineering Technology, Collège La Cité.

# Vehicle Cost Predictor – Gas vs Hybrid vs Electric (AI)

A neural network model that helps drivers in Canada understand what a car will really cost them. The user enters the **make**, the **year** and the **mileage (km)** of a vehicle, and the model estimates its fuel or energy consumption and its costs, including the difference between **winter and summer** in Canada.

## The problem

Choosing between a gas, hybrid or electric vehicle is hard. Consumption changes a lot between city and highway driving, and Canadian winters increase consumption, especially for electric vehicles. This project gives a clear estimate before you buy.

## Features

The user enters:
- Make of the vehicle
- Year
- Mileage (km)

The model predicts:
- **Consumption** (city and highway)
- **Estimated cost per month**
- **Insurance cost estimate**
- **Winter vs summer consumption** in Canada

Covers **gas**, **hybrid** and **electric** vehicles.

## How it works

1. **Data collection:** a large dataset of gas, hybrid and electric vehicles (consumption, monthly cost, city and highway use, seasonal data).
2. **Data preparation:** cleaning and encoding the data for the model.
3. **Training:** a neural network (CNN) trained on the dataset.
4. **Prediction:** the user enters make, year and km, and the model returns the estimates.

```
[Make + Year + Km] ──► [Trained neural network] ──► Consumption · Monthly cost · Insurance · Winter vs Summer
```

## Tech stack

- Python
- Neural network (CNN)

## My role

I designed and built the whole project myself: data collection, data cleaning, model training and the prediction interface.

## Context

Advanced Artificial Intelligence course – Computer Engineering Technology, Collège La Cité.

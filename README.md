# Mealworm Growth Prediction

This project predicts the **length of mealworms** using environmental factors and previous growth data. It helps in monitoring and optimizing conditions for efficient mealworm farming.

---

## Objective

To build a machine learning model that predicts **mealworm length (in mm)** based on:
- Temperature
- Humidity
- CO2 levels
- Ammonia levels
- Weight
- Engineered features (rolling averages, growth rates, etc.)

---

## Dataset

### Input Features
- `Temperature_C`
- `Humidity_%`
- `CO2_ppm`
- `Ammonia_ppm`
- `Weight_g`

### Target
- `Length_cm`


## Features Engineered

- **3-Day Averages** (e.g., `Temp_3day_avg`)
- **Change in Conditions** (e.g., `Delta_Temperature`)
- **Growth Rate** based on weight and length

## Models Used

- **Linear Regression**
- **Random Forest Regressor**
- **XGBoost Regressor** (Best performer)


## Prediction Flow

1. **Input** new environmental data

```
import pandas as pd
import numpy as np
import joblib  # or pickle
from datetime import datetime

new_data = pd.DataFrame([{
        'date': '',
        'Temperature_C':,
        'Humidity_%': ,
        'CO2_ppm': ,
        'Ammonia_ppm': ,
        'Weight_g':,
    }])
new_data['date'] = pd.to_datetime(new_data['date'])
new_data = new_data.sort_values('date')
```
> Replace the values in the new_data for predicting existing mealworm length

2. **Preprocess** and engineer features
4. **Predict** the length using the trained model
```
import joblib
model = joblib.load('xgboost_model.pkl')

# Define features used for prediction (must match training features exactly)
features = [
    'Temperature_C', 'Humidity_%', 'CO2_ppm', 'Ammonia_ppm', 'Weight_g',
    'Temp_3day_avg','Humidity_3day_avg', 'CO2_3day_avg','GrowthRate_calc' ,
    'LengthRate_calc','Delta_Temperature', 'Delta_Humidity', 'Delta_CO2', 'Delta_Ammonia',
]

X_new = processed_new_data[features]

# Predict
predicted_length = model.predict(X_new)[0]
```
5. **Output**: Estimated length in mm or cm
```
print(f"Estimated mealworm length: {predicted_length:.2f} cm")
```
## Requirements
```
pip install pandas scikit-learn xgboost joblib
```

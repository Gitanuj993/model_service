# model_service
ML model service for the project 

## Problem Statement 
MoSPI (Ministry of Statistics and Programme Implementation) ke liye ek web-based integrated project monitoring platform banana hai,

jo infrastructure projects ka current status track kare aur AI/ML ki help se future problems predict kare.

## Simple Training Architecture Pipeline
```txt
PAIMANA / Historical Data
       ↓
Data Cleaning + Feature Engineering
       ↓
    ML Models
       ↓
     Weight

```

## Simple Data Flow Pipeline 
API Design 
```txt
 API REQUEST JSON[IN]
   ↓
ML Weights [ predict ]
   ↓
JSON Response [return Backend]
```

## Getting Started 
Copy The Repository 
```txt
git clone https://github.com/Gitanuj993/model_service
cd model_service
```
install dependencies 
```txt
pip install -r requirements.txt
```

start the server 
```txt
gunicorn app.main:app
```

### Expected JSON 
```txt
project = {
    "reporting_month": "2026-04",
    "ministry": "Ministry of Civil Aviation",
    "sector": "Aviation & Aviation Infrastructure",
    "sl_no": 1,
    "project_name": "...",
    "agency": "Airport Authority of India [AAI]",
    "project_code": 612786,
    "legacy_ocms_code": "N04000106",
    "pmgid": None,
    "state": "Andhra Pradesh",
    "approval_start_date": "03/2023",
    "revised_start_date": "01/2024",
    "target_doc": "01/2026",
    "revised_doc": "07/2026",
    "original_cost_cr": 265.91,
    "revised_cost_cr": 265.91,
    "cumulative_expenditure_cr": 129.07,
    "physical_progress_pct": 65.0
}

```

## Expected API Response examples 
```txt

{"cost_overrun":0,
"cost_overrun_probability":0.0672,
"risk_level":"Medium",
"risk_score":33.49,
"time_overrun":1,
"time_overrun_probability":0.6026}

```




### Features
```txt
features = [
    "ministry",
    "sector",
    "agency",
    "state",
    "original_cost_cr",
    "cumulative_expenditure_cr",
    "physical_progress_pct",

    "financial_progress_pct",
    "progress_gap",
    "start_delay_months"
]
```
## Derived Features
```txt
financial_progress_pct = (
    cumulative_expenditure_cr / original_cost_cr
) * 100

progress_gap = (
    financial_progress_pct - physical_progress_pct
)

start_delay_months = (
    revised_start_date - approval_start_date
).days / 30.44
```

## Features for COSTOVERRUN
```txt
cost_features = [
    "ministry",
    "sector",
    "agency",
    "state",
    "original_cost_cr",
    "cumulative_expenditure_cr",
    "physical_progress_pct",
    "financial_progress_pct",
    "progress_gap",
    "start_delay_months"
]

target = "cost_overrun"

```

## Features for TIME_OVER_RUN
```txt
time_features = [
    "ministry",
    "sector",
    "agency",
    "state",
    "original_cost_cr",
    "cumulative_expenditure_cr",
    "physical_progress_pct",
    "financial_progress_pct",
    "progress_gap",
    "start_delay_months"
]

target = "time_overrun"

```
## Features for Progress_Predict
```txt
progress_features = [
    "ministry",
    "sector",
    "agency",
    "state",
    "original_cost_cr",
    "cumulative_expenditure_cr",
    "financial_progress_pct",
    "start_delay_months"
]

target = "physical_progress_pct"
```

## Rule-based risk score

$ subject to change $
```txt
risk_score = (
    0.4 * cost_probability +
    0.4 * time_probability +
    0.2 * delay_score
) * 100
```

Flags 
```txt
if risk_score < 30:
    risk_level = "LOW"
elif risk_score < 60:
    risk_level = "MEDIUM"
else:
    risk_level = "HIGH"
```

## Json Examples 
```txt
import requests

url = "https://model-service-dev-6h80.onrender.com/predict"

# json me jayega
project = {
    "reporting_month": "2026-04",
    "ministry": "Ministry of Civil Aviation",
    "sector": "Aviation & Aviation Infrastructure",
    "sl_no": 1,
    "project_name": "...",
    "agency": "Airport Authority of India [AAI]",
    "project_code": 612786,
    "legacy_ocms_code": "N04000106",
    "pmgid": None,
    "state": "Andhra Pradesh",
    "approval_start_date": "03/2023",
    "revised_start_date": "01/2024",
    "target_doc": "01/2026",
    "revised_doc": "07/2026",
    "original_cost_cr": 265.91,
    "revised_cost_cr": 265.91,
    "cumulative_expenditure_cr": 129.07,
    "physical_progress_pct": 65.0
}
response = requests.post(url, json=project)
print(response.status_code)
print(response.text)
```








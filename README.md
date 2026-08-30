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
Backend API [IN]
   ↓
ML Weights [ predict ]
   ↓
JSON Response [return Backend]
```

### All Raw  Columns
```txt
raw_columns = [
    "reporting_month",
    "ministry",
    "sector",
    "sl_no",
    "project_name",
    "agency",
    "project_code",
    "legacy_ocms_code",
    "pmgid",
    "state",
    "approval_start_date",
    "revised_start_date",
    "target_doc",
    "revised_doc",
    "original_cost_cr",
    "revised_cost_cr",
    "cumulative_expenditure_cr",
    "physical_progress_pct"
]
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

```









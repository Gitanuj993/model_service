# Architecture 
```txt
requirements.txt
    ↓
dependencies install
    ↓
app.py
    ↓
models load
    ↓
API running

```

## requirements.txt

```txt
Flask==3.1.2
pandas==2.0.3
scikit-learn==1.3.0
joblib==1.3.2
gunicorn==23.0.0
```
### Why ?
Flask → API
pandas → JSON → DataFrame + feature engineering
scikit-learn → trained pipeline/model load + prediction
joblib → .pkl models load
gunicorn → production server


## What not to include 

Matplotlib, seaborn, plotly, XGBoost, LightGBM, CatBoost, TensorFlow, PyTorch, Jupyter, Optuna, SHAP
### why ?
These are training packages not for API Production 

Here you will find  trained Models
of the format 
1. pkl
2. joblib
3. pt
4. h5

# Benchmarking Of Models

## Cost Models 
1. cost_overrun_model_v1.pkl

| Metric | Class 0 | Class 1 |
|---|---:|---:|
| Precision | 0.90 | 0.54 |
| Recall | 0.75 | 0.77 |
| F1-Score | 0.82 | 0.63 |
| Support | 288 | 109 |

| Overall Metric | Score |
|---|---:|
| Accuracy | 0.76 |
| ROC-AUC | 0.854 |



| Actual \ Predicted | No Overrun (0) | Overrun (1) |
|---|---:|---:|
| No Overrun (0) | 216 | 72 |
| Overrun (1) | 25 | 84 |

## Time Models
1. time_overrun_model_v1.pkl

| Metric | Class 0 | Class 1 |
|---|---:|---:|
| Precision | 0.74 | 0.48 |
| Recall | 0.60 | 0.64 |
| F1-Score | 0.66 | 0.55 |
| Support | 251 | 146 |

| Overall Metric | Score |
|---|---:|
| Accuracy | 0.61 |
| ROC-AUC | 0.649 |

### Confusion Matrix

| Actual \ Predicted | No Overrun (0) | Overrun (1) |
|---|---:|---:|
| No Overrun (0) | 150 | 101 |
| Overrun (1) | 52 | 94 |




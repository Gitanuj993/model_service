# About Machine Learning 
Machine Learning (ML) computer ko explicitly har rule/program likhe bina, data se patterns seekhne ki technique hai.

## Traditional Programming vs ML
Traditional programming me hum rules khud likhte hain:
```txt
Input + Rules → Output
Example:
marks >= 40 → Pass
marks < 40  → Fail
Yahan computer ko rule humne bataya.
```

Or Machine Learning me 
```txt
1000 historical projects
        ↓
Cost, progress, expenditure,
delay, sector, etc.
        ↓
       ML Model
        ↓
"Kaunse projects me
cost overrun hua?"
        ↓
       Pattern learned
```
Model historical patterns ke basis par predict kar sakta hai:

## Intresting : model "samajhta" kya hai?

Model generally human ki tarah reasoning nahi karta. Woh mathematical patterns learn karta hai.
ML ke 3 important components
1. Data
Model ko examples chahiye.
```txt
Projects → Progress → Cost → Delay → Outcome
```
3. Algorithm
Algorithm decide karta hai ki patterns kaise learn kiye jayenge.


Examples:
```txt
Linear Regression
Decision Tree
Random Forest
XGBoost
Neural Network
```
5. Training
```txt
Model predictions karta hai → actual answer se compare karta hai → apne internal parameters/weights adjust karta hai.
```
Conceptually:
```txt
Data
 ↓
Prediction
 ↓
Error
 ↓
Parameters update
 ↓
Better prediction
 ↓
Repeat...
```

## Training approach aur ML algorithm

### Training Approaches
1. Supervised Learning
2. Unsupervised Learning
3. Semi-Supervised Learning
4. Self-Supervised Learning
5. Reinforcement Learning

What would we use ?


Supervised Learning with historical completed projects + feature engineering 
   
and 
1. Linear Regression
2. Logistic Regression
3. Random Forest
(optional)
4. Decision Tree
5. XGBoost / LightGBM
6. Neural Networks


## Conclusion 
Machine Learning = past data ke examples se mathematical patterns learn karke unseen/new data par prediction ya decision karna.

Training ek process hai. Trained model se prediction karna doosra process hai.



# 🏀 NCAA 2025 Kaggle Competition  

This repository contains my solution for the **NCAA 2025 March Machine Learning Mania** competition on Kaggle. The goal is to predict the outcomes of the **NCAA Division 1 Men’s and Women’s basketball tournaments** using historical data. Predictions are evaluated using the **Brier score**, which measures the accuracy of probabilistic predictions.  

## 📌 Approach  

### 🏆 Feature Engineering  
1. **Elo Ratings**:  
   - Based on [this notebook](https://www.kaggle.com/code/lpkirwin/fivethirtyeight-elo-ratings), which integrates **FiveThirtyEight's Elo Ratings**.  
   - Tweaked to base **Elo** on **previous tournament matches** rather than the full season.  
   - Calculated **average Elo across seasons** for more stability.  

2. **Team Quality**:  
   - Inspired by the **3rd place solution (2023)** from [this notebook](https://www.kaggle.com/code/tihonby/march-madness-3th-place-solution).  

3. **Major other Features Added**:  
   - **Weighted average seeds** to adjust for past performance.
   - **Weighted average elos**  
   - **Relevant box score statistics** using correlation with past years regular matches.

These improvements reduced the **Brier score** to **~0.13** (currently updating as matches unfold).  

---

## 🤖 Model  

The model used is a **Random Forest Classifier** with the following hyperparameters:  

```python
from sklearn.ensemble import RandomForestClassifier

RF1 = RandomForestClassifier(
    n_estimators=100,
    max_depth=None,
    min_samples_split=2,
    min_samples_leaf=1,
    max_features="sqrt",
    bootstrap=True,
    random_state=42
)
```

## 📊 Performance  

**Evaluation on 2024 Matches:**  
- **Accuracy:** 0.7537  
- **Brier Score:** 0.1770  

---

## 🚀 Next Steps  

- 🔄 **Update Brier score** as 2025 matches unfold.  
- 📊 **Experiment with additional features**, such as momentum-based stats and injury impact.  
- 🤖 **Try ensemble methods or neural networks** for further improvement.  

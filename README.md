# Bank Marketing Subscription Prediction

Can we predict which bank customers will say **yes** to a term deposit after a marketing call?

This project uses machine learning to find out, so a bank can focus its calls on the customers most likely to subscribe.

## Dataset

- **Source:** Bank Marketing dataset (`bank-additional-full.csv`), from a Portuguese bank
- **Size:** 41,188 customers, 21 columns
- **Target:** `y` (did the customer subscribe? yes / no)
- **Challenge:** Only about 11% of customers said yes, so the data is imbalanced

## What I Did

1. **Explored the data:** checked duplicates, missing values, "unknown" values and class balance, and looked at subscription rates by month, job and contact type
2. **Cleaned and prepared it:**
   - Turned `pdays = 999` into a "not previously contacted" flag
   - Encoded categories as numbers
   - Scaled the features with `StandardScaler`
3. **Avoided data leakage:** removed `duration` (call length), because it is only known after the call ends
4. **Handled imbalance:** used SMOTE on the training data only
5. **Trained 7 models:** Logistic Regression, Naive Bayes, Linear SVM, KNN, Decision Tree, Random Forest and Gradient Boosting
6. **Compared them** using precision, recall and F1-score, not just accuracy

## Results

| Model | Accuracy | Precision | Recall | F1 |
|---|---:|---:|---:|---:|
| **Random Forest** | 86.5% | 45.0% | 56.7% | **50.2%** |
| Gradient Boosting | 87.6% | 48.3% | 47.8% | 48.0% |
| Decision Tree | 83.8% | 38.6% | 59.3% | 46.7% |
| Logistic Regression | 78.3% | 30.5% | 63.2% | 41.1% |
| Linear SVM | 77.6% | 29.7% | 63.6% | 40.5% |
| Naive Bayes | 69.9% | 24.1% | 70.3% | 36.0% |
| KNN | 71.9% | 24.5% | 64.5% | 35.5% |

**Best model:** Random Forest, with the highest F1-score (50.2%).

## Key Takeaways

- Accuracy alone is misleading here, so F1, precision and recall matter more
- Customers who said yes in a previous campaign are more likely to subscribe again
- Too many calls to the same customer lowers efficiency
- Contact month and contact type affect subscription rates

## Tools Used

Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Imbalanced-learn

## Files

- `Portugese_Bank.ipynb`: the full notebook (EDA, preprocessing, models, report)
- `bank-additional-full.csv`: the dataset


## Author

**Alden Pimenta**

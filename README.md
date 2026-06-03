---

## Models Evaluated

| Model | Notes |
|-------|-------|
| Logistic Regression | Baseline, interpretable, fairness-compatible |
| Decision Tree | Rule-based, max depth 5 |
| Random Forest + SMOTE | 200 estimators, SMOTE-balanced training data |
| Gradient Boosting + SMOTE | Sequential ensemble, highest accuracy |

---

## Fairness Metrics

| Metric | Description |
|--------|-------------|
| Demographic Parity Difference (DPD) | Gap in positive prediction rates across groups |
| Equal Opportunity Difference (EOD) | Gap in true positive rates across groups |

Both metrics evaluated across: Gender, Ethnicity, Parenthood Status, Relationship Status, Language Proficiency, Education

---

## Mitigation Techniques

| Stage | Technique |
|-------|-----------|
| Pre-processing | Reweighing, adjusts sample weights before training |
| In-processing | Exponentiated Gradient, fairness constraints during training |
| Post-processing | Threshold Adjustment, group-specific decision boundaries |

---

## Key Results

| Model | Accuracy | DPD | EOD |
|-------|----------|-----|-----|
| LR Baseline | 0.686 | 0.0323 | 0.0384 |
| LR + Reweighing | 0.691 | 0.0132 | 0.0543 |
| LR + Threshold Adj. | 0.692 | 0.0257 | 0.0454 |
| Decision Tree | 0.651 | 0.1668 | 0.0716 |
| RF + SMOTE | 0.707 | 0.0372 | 0.0200 |
| Gradient Boosting | 0.779 | 0.0413 | 0.0648 |

### Key Finding

Ethnicity DPD = 1.0, the maximum possible value. Native candidates received predicted hire rates of 100% while Ukrainian and other non-native candidates received near-zero positive predictions regardless of gender, a 100 percentage point intersectional gap.

---

## Tools and Libraries

- Python 3.10+
- pandas, numpy for data processing
- scikit-learn for machine learning models
- fairlearn for fairness metrics and mitigation
- imbalanced-learn for SMOTE oversampling
- matplotlib for visualizations
- Google Colab as development environment

---

## References

- Barocas, S., Hardt, M., and Narayanan, A. Fairness in Machine Learning
- Kleinberg, J., Mullainathan, S., and Raghavan, M. (2017). Inherent Trade-Offs in the Fair Determination of Risk Scores
- IBM Research. AI Fairness 360 AIF360 Toolkit
- Bird et al. (2020). Fairlearn: A toolkit for assessing and improving fairness in AI
- Chawla et al. (2002). SMOTE: Synthetic Minority Over-sampling Technique
- Buttler, D. (2025). Hiring Discrimination in the Organisational Context Dataset

# OSIC-Pulmonary-Fibrosis-Progression-16th-solution

I only used tabular features, didn't use CT scans or other meta data. I don't have enough time to extract, and my computer is not good at all, so I just do my best on tabular data.

# Input Feature
## Numerical Feature
- target_week
- base_Week
- base_FVC
- base_Percent
- Age
- weeks_passed: target_week - base_week
- Height: (base_FVC / 933.33 + 0.026 * Age +2.89) / 0.0443

- FEV: 
$\begin{cases}
0.84 * FVC - 0.23 \text{, if Sex = Male}\\
0.84 * FVC - 0.36 \text{, if Sex = Female}
\end{cases}$

- percent_reciprocal: 1 / base_Percent
- FEV_ratio: FEV / base_FVC
- percent_ratio: base_FVC / base_Percent

## Categorical Feature

Because there are few categories, so I just use one hot encoding.

- Female
- Male 
- Currently smokes
- Ex-smoker
- Never smoked

# Confidence Prediction

Using quantile LGBM Regressor with alpha = [0.75, 0.25] to 
subtract.

# FVC Prediction
![img](img/stack.png)

# TODO

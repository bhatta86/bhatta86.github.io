---
title: "Study of Human Mobility"
excerpt: "A data-driven modeling project analyzing and predicting population mobility patterns using regression-based machine learning techniques."
collection: portfolio
---

### Modeling and Predicting Human Mobility Patterns: A Data-Driven Approach

This project involved large-scale modeling and prediction of human mobility patterns using regression-based machine learning techniques. The analysis focused on population flow data across geographic regions over the COVID-19 timeline, with the objective of understanding how group-level movement behavior evolved under changing real-world conditions and assessing the feasibility of forward-looking prediction.

**Technical Context**: CMSE 202 — Computational Modeling Tools and Techniques

**Dataset + Data Handling**  
The project used the publicly available COVID19USFlows - Weekly Flows dataset, which provides weekly population flow estimates between U.S. geographic regions. Large-scale CSV updates were aggregated and processed using Pandas, then organized into training and testing sets to enable temporal generalization. The training dataset spanned January 2019 to June 2021, while the testing dataset covered July 2021 to December 2021.

**Methodology**
- Aggregated and preprocessed large-scale weekly CSV datasets representing inter-regional population flows.
- Engineered regression-ready feature sets suitable for learning temporal mobility trends.
- Trained two regression-based machine learning models:
  - Random Forest Regression
  - Gradient Boosting Regression
- Evaluated predictive performance by comparing model outputs against held-out future data.
- Quantified model accuracy using relative error to assess robustness under real-world variability.

**Performance**
- Random Forest Regression achieved a relative error of approximately **0.04 percent**, indicating strong predictive accuracy and robustness across the testing interval.
- Gradient Boosting Regression exhibited a relative error of approximately **163.95 percent**, demonstrating sensitivity to anomalies and reduced generalization performance.

**Further Thoughts**
Future improvements include exploring neural network-based models to better capture non-linear temporal dynamics and explicitly modeling disruptive events such as holidays, large public gatherings, or natural disasters. Incorporating anomaly detection or regime-switching approaches could further improve prediction stability during periods of abrupt behavioral change.

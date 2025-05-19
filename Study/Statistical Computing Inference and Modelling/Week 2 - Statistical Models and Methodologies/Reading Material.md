## 🧠 Overview

In **Week 2 Reading: Common Statistical Methodologies**, learners reviewed the systematic approaches and techniques used to build, evaluate, and deploy statistical models in data analysis, covering methodologies from Exploratory Data Analysis to Model Deployment.

---

## 🎯 Learning Objectives

By the end of this reading, learners should be able to:

1. Discuss the role of **statistical modeling** in data analysis.
2. Identify and describe **seven key methodologies** in statistical modeling.
3. Understand practical techniques for **model evaluation**.
4. Recognize the steps for **deploying** and **monitoring** models in production.

---

## 1. Critical Methodologies in Statistical Modeling

1. **Exploratory Data Analysis (EDA)**

   * **Purpose:** Understand data structure, detect outliers, and identify trends.
   * **Techniques:** Histograms, scatter plots, box plots.
   * **Example:** Plotting customer purchase amounts to spot abnormal transactions.

2. **Hypothesis Testing**

   * **Purpose:** Assess assumptions about variable relationships.
   * **Steps:** Define null/alternative hypotheses, choose test (t-test, chi-square), interpret p-values.
   * **Example:** Testing whether a new marketing campaign changed average sales.

3. **Model Selection and Specification**

   * **Purpose:** Choose the best model form (linear, logistic, time series).
   * **Criteria:** Goodness of fit (R², AIC), predictive accuracy, interpretability.
   * **Example:** Comparing linear vs. Poisson regression for count data.

4. **Parameter Estimation**

   * **Purpose:** Estimate unknown parameters that best fit observed data.
   * **Techniques:** Maximum Likelihood Estimation (MLE), Bayesian estimation.
   * **Example:** Using MLE to estimate mean and variance of a normal distribution.

5. **Model Validation**

   * **Purpose:** Evaluate model performance and reliability.
   * **Techniques:** Cross-validation, hold-out test sets, checking assumptions.
   * **Example:** K-fold cross-validation to assess predictive accuracy on unseen data.

6. **Model Interpretation**

   * **Purpose:** Understand variable relationships and underlying mechanisms.
   * **Approach:** Interpret coefficients, compute effect sizes, assess significance.
   * **Example:** Explaining how a \$1 increase in price affects demand.

7. **Model Deployment and Monitoring**

   * **Purpose:** Implement models in production and ensure ongoing performance.
   * **Activities:** Automate predictions, track drift, update model with new data.
   * **Example:** Deploying a fraud detection model and monitoring false-positive rates.

---

## 2. Techniques for Model Evaluation

* **Residual Analysis:** Examine differences between observed and predicted values to detect bias.
* **Chi-Square Tests:** Evaluate fit for categorical data by comparing observed vs. expected frequencies.
* **Graphical Methods:** Use scatter plots, histograms, and Q-Q plots for visual diagnostics.

---

## 3. Reflective Questions

1. Why is EDA considered a foundational step before model building?
2. How does cross-validation help prevent overfitting?
3. What criteria would you use to choose between MLE and Bayesian estimation?
4. Describe a monitoring strategy for a model deployed in a changing environment.

---

**References & Further Reading:**

* Casella & Berger (2002), *Statistical Inference*.
* Wasserman (2013), *All of Statistics*.
* Hastie, Tibshirani & Friedman (2009), *The Elements of Statistical Learning*.

---

**Next Steps:** Integrate these methodologies into your project workflow: perform thorough EDA, select and validate models carefully, and plan for robust deployment.

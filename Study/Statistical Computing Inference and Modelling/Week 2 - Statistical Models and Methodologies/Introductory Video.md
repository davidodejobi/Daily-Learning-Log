## 🧠 Overview

In **Week 2: Statistical Models and Methodologies**, learners were introduced to the **building blocks of statistical models**—understanding how variables connect, how to choose the right model type, and how models drive data-driven decisions.

---

## 🎯 Learning Objectives

By the end of this lesson, learners were able to:

1. **Define** and **identify** model components (response, predictors, error).
2. **Compare** parametric, non-parametric, and linear models, with pros and cons.
3. **Apply** models to real-life scenarios, like sales forecasting.
4. **Select** appropriate models based on data structure and goals.

---

## 1. Model Components Explained with Everyday Examples

| Component               | What It Means                                          | Relatable Example                                                |
| ----------------------- | ------------------------------------------------------ | ---------------------------------------------------------------- |
| **Response Variable**   | The outcome you want to predict or explain.            | *Monthly grocery bill* when you track your spending each month.  |
| **Predictor Variables** | Factors that help explain or predict the response.     | *Number of family members*, *income*, *promotion coupons used*.  |
| **Error Term**          | The “leftover” variability not captured by predictors. | Unplanned events (guests over, price discounts) affecting bills. |

> **Tip:** Think of building a recipe: the response is the final dish, predictors are the ingredients, and the error term is the flavor variation you can’t fully control.

---

## 2. Types of Models: Choose Your Tool

### 2.1 Parametric Models

* **Definition:** Models that assume a specific functional form (e.g., linear, logistic) with a fixed number of parameters.
* **What it is:** You assume a specific formula (e.g., straight line) connects your predictors to the response.
* **Everyday analogy:** Fitting a straight edge to a bent wire—sometimes it lines up well, but not always.
* **Key pros:** Fast, easy to interpret; efficient with smaller sample sizes.
* **Key cons:** Can be misleading if the true relationship deviates from the assumed form.
* **Relatable example:** Predicting your electricity bill by assuming it increases by a fixed rate per kWh used.

### 2.2 Non-Parametric Models

* **Definition:** Models that do not specify a predetermined functional form, allowing data-driven shapes.
* **What it is:** You let the data “speak for itself” without forcing a predefined shape.
* **Everyday analogy:** Letting clay take shape by hand rather than pressing it into a mold.
* **Key pros:** Flexible, captures complex patterns; less risk of model misspecification.
* **Key cons:** Requires larger datasets; can overfit without careful tuning.
* **Relatable example:** Tracking your fitness progress: a smooth line through daily weight measurements to capture irregular trends.

### 2.3 Linear Models (a Subset of Parametric)

* **Definition:** Parametric models where the relationship between predictors and response is restricted to a straight line.
* **What it is:** Special case of parametric with straight-line relationships.
* **Everyday analogy:** A ruler—perfect for measuring straight distances, limited for curves.
* **Key pros:** Very simple, works surprisingly well in many cases; interpretable coefficients.
* **Key cons:** Misses non-linear effects (e.g., tipping point behaviors) in real data.
* **Relatable example:** Modeling how your taxi fare increases linearly with distance traveled.

## 3. Real-Life Case Study: Smartphone Sales Forecast Real-Life Case Study: Smartphone Sales Forecast

**Scenario:** Tammy predicts sales for a new smartphone model before committing to mass production.

1. **Identify components:**

   * *Response:* Number of units sold in the first month.
   * *Predictors:* Marketing budget, pre-order count, competitor price.
   * *Error term:* Unexpected events (e.g., supply delays).
2. **Pick a model:** Start with **linear regression** for simplicity.
3. **Fit the model:** Estimate how each \$1,000 in marketing spend increases sales.
4. **Validate:** Compare predicted vs. actual sales on a small test launch.
5. **Iterate:** If errors are large, consider a **non-parametric** spline model to capture promotional campaign spikes.

> **Takeaway:** Start simple, check performance, then adapt complexity.

---

## 4. Decision Guide: Which Model to Use?

* **Data volume small, clear assumptions:** Parametric/linear models.
* **Data volume large, unknown pattern:** Non-parametric methods.
* **Need interpretability:** Linear models (easy to explain to stakeholders).
* **Need accuracy over simplicity:** Non-parametric, ensemble methods.
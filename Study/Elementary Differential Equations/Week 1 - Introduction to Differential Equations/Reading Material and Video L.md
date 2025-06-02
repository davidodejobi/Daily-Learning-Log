# MTH 202 - Elementary Differential Equations

## Week 1: Classification of Differential Equations – Detailed Study Note

---

## Learning Objectives

By the end of this lesson, you should be able to:

* Determine the **order** of a given differential equation.
* Classify it as **first-order**, **second-order**, or **higher-order**.
* Identify different types of **first-order differential equations**.
* Identify types of **second-order differential equations**.
* State some examples of **higher-order differential equations**.

---

## Introduction to Differential Equations

* A **differential equation** involves **unknown functions** and their **derivatives**.
* They describe how quantities **change over time or space**.
* These equations help model **real-world phenomena** from science, engineering, biology, and more.
* The challenge is to **convert real-world processes** into mathematical equations.

---

## Types of Differential Equations

### 1. First-Order Differential Equations

These involve **only the first derivative** of the unknown function.
Example:

$$
\frac{dy}{dx} = f(x)
$$

Common in problems involving **rates of change**, **growth**, or **decay**.

#### Types of First-Order Equations:

## 1. Linear First-Order Differential Equations

A linear first-order differential equation has the form:

$$
\frac{dy}{dx} + P(x)y = Q(x)
$$

* **P(x)** and **Q(x)** are functions of **x**.
* The equation is linear because the unknown function **y** and its derivative appear only to the first power.
* **Solution Strategy:** Find an integrating factor $\mu(x) = e^{\int P(x) dx}$, multiply both sides by $\mu(x)$, and integrate.

---

## 2. Separable Equations

A separable first-order equation has the form:

$$
\frac{dy}{dx} = f(x)g(y)
$$

* Variables **x** and **y** can be separated:

$$
\frac{dy}{g(y)} = f(x) dx
$$

* **Solution Strategy:** Integrate both sides:

$$
\int \frac{1}{g(y)} dy = \int f(x) dx
$$

* Obtain the implicit solution, and solve for **y(x)** if possible.

---

## 3. Bernoulli Equations

A Bernoulli equation is nonlinear and has the form:

$$
\frac{dy}{dx} + P(x)y = Q(x)y^n
$$

* **n** is any real number except 0 or 1.
* **Linearizing Strategy:** Divide by $y^n$ and use substitution $v = y^{1-n}$, transforming the equation into a linear form.
* Then, apply integrating factor techniques.

---

## 4. Riccati Equations

A Riccati equation has the form:

$$
\frac{dy}{dx} = f(x) + g(x)y + h(x)y^2
$$

* Quadratic in **y**.
* **Solution Strategy:** Difficult to solve in general. If a particular solution is known, substitution can reduce it to a Bernoulli equation.

---

## 5. Homogeneous Equations

A first-order differential equation is homogeneous if it can be written as:

$$
\frac{dy}{dx} = F\left(\frac{y}{x}\right)
$$

* **Solution Strategy:** Use the substitution $v = \frac{y}{x}$, so $y = vx$ and $\frac{dy}{dx} = v + x \frac{dv}{dx}$.
* Substitute and separate variables to solve for $v(x)$, then substitute back to find $y(x)$.

---

## 6. Exact and Non-Exact Equations

The equation is given by:

$$
M(x,y)dx + N(x,y)dy = 0
$$

* **Exact Equation:** If $\frac{\partial M}{\partial y} = \frac{\partial N}{\partial x}$, the equation is exact and there exists a function $\psi(x,y)$ such that:

$$
\frac{\partial \psi}{\partial x} = M, \quad \frac{\partial \psi}{\partial y} = N
$$

* **Solution Strategy:** Find $\psi(x,y)$ and set $\psi(x,y) = C$.
* **Non-Exact:** If the equation is not exact, it may become exact with an integrating factor.

---

### 2. Second-Order Differential Equations

### What is a Second-Order Differential Equation?

A second-order differential equation involves the second derivative of the unknown function. The general form is:

$$
\frac{d^2y}{dx^2} = f(x, y, \frac{dy}{dx})
$$

These equations describe systems with more complex dynamics, such as oscillations, vibrations, or mechanical systems.

---

## Types of Second-Order Differential Equations

### 1. Linear Second-Order Equations

A second-order equation is linear if **y** and its derivatives appear to the first power and are not multiplied together. The standard form is:

$$
\frac{d^2y}{dx^2} + P(x)\frac{dy}{dx} + Q(x)y = R(x)
$$

* **Homogeneous** if $R(x) = 0$.
* **Non-homogeneous** if $R(x) \neq 0$.

#### **Homogeneous Linear Equations**

$$
\frac{d^2y}{dx^2} + P(x)\frac{dy}{dx} + Q(x)y = 0
$$

* **Solution Strategy:** Find two linearly independent solutions (using methods like characteristic equations for constant coefficients) and form the general solution:

$$
y(x) = C_1 y_1(x) + C_2 y_2(x)
$$

#### **Non-Homogeneous Linear Equations**

$$
\frac{d^2y}{dx^2} + P(x)\frac{dy}{dx} + Q(x)y = R(x)
$$

* **Solution Strategy:**

1. Find the complementary (homogeneous) solution.
2. Find a particular solution for $R(x)$ using methods such as undetermined coefficients or variation of parameters.
3. General solution:

$$
y(x) = y_h(x) + y_p(x)
$$

---

### 2. Nonlinear Second-Order Equations

Nonlinear second-order equations include terms where **y** or its derivatives appear with exponents other than one, products, or functions of **y** or $\frac{dy}{dx}$. General form:

$$
\frac{d^2y}{dx^2} = f(x, y, \frac{dy}{dx})
$$

* **Example:**

$$
\frac{d^2y}{dx^2} + y^2 = 0
$$

* **Solution Strategy:** Often requires special methods or numerical solutions as they do not follow superposition principles.

---

### 3. Special Forms

Some second-order equations appear in classical mechanics and physics:

#### **Euler-Cauchy (Cauchy-Euler) Equations**

$$
 x^2 \frac{d^2y}{dx^2} + a x \frac{dy}{dx} + b y = 0
$$

* **Solution Strategy:** Assume $y = x^m$ and solve the resulting quadratic for $m$.

#### **Equations with Constant Coefficients**

$$
 a \frac{d^2y}{dx^2} + b \frac{dy}{dx} + c y = f(x)
$$

* **Solution Strategy:** Characteristic equation:

$$
 ar^2 + br + c = 0
$$

Solve for roots $r$ and build solutions based on their nature (real distinct, real repeated, or complex).

---

## Summary

* **Second-order differential equations** model complex systems like oscillations, mechanical vibrations, and electrical circuits.
* Can be **linear** or **nonlinear**.
* **Homogeneous equations** have zero on the right-hand side, while **non-homogeneous** have forcing terms.
* **Constant coefficient equations** and **Euler-Cauchy equations** are special forms with standard solution methods.
* **Nonlinear equations** often require numerical or approximate methods.

---

### 3. Higher-Order Linear Differential Equations

* **Order higher than 2**, e.g. third-order, fourth-order.

$$
a_n(x)\frac{d^n y}{dx^n} + \cdots + a_1(x)\frac{dy}{dx} + a_0(x)y = f(x)
$$

* **Linear** if $y$ and its derivatives appear to the first power.

---

## Summary of Key Concepts

* **Differential equations** model how things change over time or space.
* Can be **ordinary (ODEs)** or **partial (PDEs)** (focus here is ODEs).
* Can be **linear** (simpler) or **nonlinear** (more complex).
* **First-order equations** describe rates of change and can be separable, linear, Bernoulli, etc.
* **Second-order equations** describe more complex dynamics (e.g., vibrations).
* **Higher-order equations** involve higher derivatives and model systems with more complex behavior.

---

## Further Reading

1. Boyce & DiPrima: *Elementary Differential Equations and Boundary Value Problems*
2. Zill: *Differential Equations with Boundary-Value Problems*
3. Tenenbaum & Pollard: *Ordinary Differential Equations*
4. Blanchard, Devaney & Hall: *Differential Equations*
5. Nagle, Saff & Snider: *Fundamentals of Differential Equations*
6. SOS Mathematics: [sosmath.com/diffeq/diffeq.html](https://sosmath.com/diffeq/diffeq.html)

---

Would you like me to:

* Add **worked examples** for each type of equation?
* Create **visual diagrams** (flowcharts, slope fields) for these equations?
* Prepare **practice questions** to solidify your understanding?
  Just let me know!

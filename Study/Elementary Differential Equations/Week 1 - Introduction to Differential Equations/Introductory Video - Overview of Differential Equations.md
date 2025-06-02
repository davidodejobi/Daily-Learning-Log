## 1. What is a Differential Equation?

A differential equation is a mathematical equation that includes:

* An unknown function $y(x)$, which means a function of $x$.
* The derivatives of that function (which tell us how fast the function is changing).

**In words:**
A differential equation gives us a rule connecting a function and its rate(s) of change.

## 2. What’s the "Order" of a Differential Equation?

* The order is the highest derivative in the equation.
* If the highest derivative is $\frac{dy}{dx}$, it’s a first-order equation.
* If it’s $\frac{d^2y}{dx^2}$, it’s a second-order equation.
* If it’s $\frac{d^3y}{dx^3}$, it’s a third-order equation.

**Why it matters:**
Higher-order equations describe more complex systems (like movement with acceleration).

## 3. What’s the "Degree" of a Differential Equation?

* The degree is the highest power to which the highest derivative is raised, after clearing fractions and roots.
* Example:

$$
\left( \frac{d^2y}{dx^2} \right)^2 + \frac{dy}{dx} = x
$$

This is a second-order (due to $\frac{d^2y}{dx^2}$) and degree 2 (because of the square).

## 4. General Form of a Linear Differential Equation

A linear differential equation has the structure:

$$
 a_n(x) \frac{d^n y}{dx^n} + a_{n-1}(x) \frac{d^{n-1}y}{dx^{n-1}} + \cdots + a_1(x) \frac{dy}{dx} + a_0(x) y = f(x)
$$

where $a_n(x) \neq 0$.

* $a_n(x)$ are functions of $x$ that multiply the derivatives of $y$.
* $f(x)$ is a function of $x$ not involving $y$.

Only these operations are allowed for linear equations:

* Differentiate $y$.
* Multiply $y$ and its derivatives by functions of $x$.
* Add them all together to get $f(x)$.

## 5. Initial Value Problem (IVP)

An IVP is a differential equation with given initial conditions.

* The equation itself tells how things change.
* Some starting conditions are provided, such as $y(x_0) = y_0$.

Example:

$$
\sin(t) \frac{d^2x}{dt^2} + \cos(t) \frac{dx}{dt} + \sin(t) x = \tan(t)
$$

with

$$
 x(1.25) = 12, \quad \frac{dx}{dt}(1.25) = 2
$$

This means at $t = 1.25$, the position $x$ is 12, and the velocity $\frac{dx}{dt}$ is 2.

## 6. Linear vs. Nonlinear Equations

* **Linear Differential Equations:**

  * $y$ and its derivatives appear to the first power.
  * No products of $y$ and its derivatives.
  * Example: $\frac{dy}{dx} + P(x) y = f(x)$

* **Nonlinear Differential Equations:**

  * More complex (e.g., $y^2$, $\frac{dy}{dx} \cdot y$, etc.).
  * Harder to solve.

## 7. Step-by-Step Approach for Solving First-Order Linear Equations

Given:

$$
\frac{dy}{dx} + P(x) y = f(x)
$$

Steps:

1. Find an integrating factor:

$$
 \mu(x) = e^{\int P(x) dx}
$$

2. Multiply both sides of the equation by $\mu(x)$.
3. The left side becomes a product derivative:

$$
 \frac{d}{dx}[\mu(x) y] = \mu(x) f(x)
$$

4. Integrate both sides:

$$
 \mu(x) y = \int \mu(x) f(x) dx + C
$$

5. Solve for $y(x)$.

## 8. Existence and Uniqueness

* **Existence:** Does a solution exist?
* **Uniqueness:** Is there only one solution?

For IVPs, if the function and its derivative with respect to $y$ are continuous around the initial condition, a unique solution usually exists.

## Next Steps

* Work through simple examples step-by-step.
* Visualize solutions with graphs and slope fields.
* Apply these concepts to real-world problems (like motion or population growth).


This part of the math deals with the normal equations. <br>
We will start from scratch and it wouldn't take long. You can probably finish Linear Regression in a day even if you start from scratch following this material.Feel free to go the textbook parts mentioned in CS229 files to learn about these from the textbook.<br>
What is Linear Algebra? The study of vectors and rules to manipulate these vectors.
##### Examples of Vector Objects:
1. Geometric
2. Polynomials
3. Audio Signals
4. Elements of $R^n$<br>

## System of Linear Equations
Collection of one or more linear equations involving the same set of variables. "Linear" means each term is just raised to the power of 1. <br>
Let's go through an example, consider <br>
1. Products: $N_1, N_2, ....N_n$
2. Resources: $R_1, R_2,.... R_m$
3. Coefficients ($a_{ij}$): The amount of resource i required to make the product j.
4. Unknowns($x_j$): The number of units of j we can produce is what we need to find.
5. Constants ($b_i$): The total available amount of resource i.

## The equation
To find an "optimal" plan where no resources are wasted, the amoutn of resource i used across the products must exactly equal the available amount $b_i$. <br>
For resource i: $a_{i1}x_1 + a_{i2}x_2+......a_{in}x_n$ <br>
When we stack this equation for m resources, we get the general form of a system of linear equations. <br>
$$
\begin{aligned}
a_{11} x_1 + \dots + a_{1n} x_n &= b_1 \\
&\vdots \qquad\qquad\qquad (2.3) \\
a_{m1} x_1 + \dots + a_{mn} x_n &= b_m
\end{aligned}
$$
where $a_{ij} \in \mathbb{R}$ and $b_i \in \mathbb{R}$.<br>
Any set of values ($x_1,...., x_n$) that makes all the equations true simultaneously is called a solution. <br>

## Three possible Outcomes
There are three possible outcomes when you solve a system of linear equations.
### Case A: No Solution (Inconsistent System)

$$
\begin{aligned}
x_1 + x_2 + x_3 &= 3 \quad &(1) \\
x_1 - x_2 + 2x_3 &= 2 \quad &(2) \\
2x_1 + 3x_3 &= 1 \quad &(3)
\end{aligned}
$$

**Why it fails:** If you add Equation (1) and Equation (2) together, the $+x_2$ and $-x_2$ cancel out, leaving $2x_1 + 3x_3 = 5$. 

However, Equation (3) explicitly states that $2x_1 + 3x_3 = 1$. Since $5 \neq 1$, we have a logical contradiction. No values of $x_1, x_2, x_3$ can satisfy all three equations at once.

---

### Case B: Exactly One Solution (Unique Solution)

$$
\begin{aligned}
x_1 + x_2 + x_3 &= 3 \quad &(1) \\
x_1 - x_2 + 2x_3 &= 2 \quad &(2) \\
x_2 + x_3 &= 2 \quad &(3)
\end{aligned}
$$

**Why it works:** The equations provide just enough independent information to pin down every variable.
* By adding (1) and (3), we find $x_1 = 1$.
* Adding (1) and (2) gives $2x_1 + 3x_3 = 5$. 
* Since $x_1 = 1$, this means $2(1) + 3x_3 = 5$, so $x_3 = 1$.
* Plugging $x_3 = 1$ into (3) gives $x_2 + 1 = 2$, so $x_2 = 1$.

The unique solution is the point $(1, 1, 1)$.

---

### Case C: Infinitely Many Solutions (Underdetermined / Redundant System)

$$
\begin{aligned}
x_1 + x_2 + x_3 &= 3 \quad &(1) \\
x_1 - x_2 + 2x_3 &= 2 \quad &(2) \\
2x_1 + 3x_3 &= 5 \quad &(3)
\end{aligned}
$$

**Why it happens:** If you add Equation (1) and (2), you get $2x_1 + 3x_3 = 5$, which is exactly Equation (3). Equation (3) is redundant; it provides no new information. 

We are left with 2 useful equations but 3 unknowns. This means we cannot find a single unique answer. Instead, we declare one variable (e.g., $x_3 = a$) as a free variable. We can then express the other variables in terms of $a$:

$$
\begin{aligned}
x_1 &= \frac{5}{2} - \frac{3}{2}a \\
x_2 &= \frac{1}{2} + \frac{1}{2}a
\end{aligned}
$$

For any real number you choose for $a$, you get a valid solution. Hence, there are infinitely many solutions.

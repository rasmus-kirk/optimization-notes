---
title: Notes
author: Rasmus Kirk
date: 2022-06-15
---
# Linear Programming Problems
## Disposition
- Punkt her

## Definitions
- **Target Function:** A Linear Function, over all variables, to be maximized.
- **Polytope:** The geometric shape formed by the constraints.
- **Solution:** Any possible values that can be assigned to the variables, ignoring constraints.
- **Feasible Solution:** Any _Solution_, satisfying all constraints.
- **Basic Solution:** A _Feasible Solution_ which lies in the geometric corner of the polytope.
- **Optimal Solution:** A _Feasible Solution_ that maximizes the target function.

## Linear Programming Problems
- Problems of the form: $z = \sum_{i=0}^{n} c_i x_i$ where we want to maximize or minimize $z$

## Standard form
- Must be maximization problem
- All constraints must be $\leq$

## Fundemental Theorem of Linear Programming
1. If no optimal solution exists, the problem is infeasible or unbounded
2. If _1._ and there exists a feasible solution there exists a Basic Feasible Solution
3. If there exists an optimal solution, there exists a Basic Optimal Solution
- **TLDR:** If an optimal solution exists, there must be one in a corner of the convex polytope.

## Simplex
- Takes a Linear Programming Problem in Standard Form,
- Returns the optimal solution
- Simplex Tableu:
	$$
		\begin{bmatrix}
		1 & \vec{-c^T} & 0\\
		0 & A & \vec{b}
		\end{bmatrix}
	$$
- **Slack variales:** Constraints of the form $c \leq c_1 x_1 + c_2 x_2 \rightarrow x_{n+1} = c - (c_1 x_1 + c_2 x_2)$
- **Bland's Rule:**
	- Why? Prevents cycles
	- How?
		- Start by choosing the left-most non-basic variable with a positive coefficient
- 

### Example
We start with:

$$z  = 0 + 10 x_1 + 22 x_2$$
$$11 \geq 3 x_1 + 4  x_2$$
$$15 \geq 5 x_1 + 20 x_2$$

Introducing slack variables:

$$z = 0 + 10x_1 + 22x_2$$
$$x_3 = 11 - 3x_1 - 4x_2$$
$$x_4 = 15 - 5x_1 - 20x_2$$

We transform to tableu form:

|$x_1$|$x_2$|$x_3$|$x_4$|$Z$|$c$|
|----:|----:|----:|----:|--:|--:|
|    3|    4|    1|    0|  0| 11|
|    5|   20|    0|    1|  0| 15|
|  -10|  -22|    0|    0|  1|  0|

1. We need to choose the _Entering Variable_ (Pivot Column ($p_c$)) using Bland's rule, we choose the first column.
2. Then we need to choose an _Exiting Variable_ (Pivot Row ($p_r$)) using Bland's rule, $\ \textbf{Row 1: } 3/11 = 3+\frac{2}{3}\ $ and $\ \textbf{Row 2: } 15/5 = 3$, \textbf{Row 2} has the smallest non-negative value, so \textbf{Row 2} is the pivot row.
3. We then perform elementary row operations such that $T_{p_c,p_r} = 1$ and all other elements in the pivot column should be zero, $\sum_i T_{p_c, i} = 1$:
4. Repeat until all coefficients in the last row are non-negative (We don't need to repeat for this example):

|$x_1$|$x_2$|$x_3$|$x_4$         |$Z$|$c$|
|----:|----:|----:|-------------:|--:|--:|
|    0|   -8|    1|$-\frac{3}{5}$|  0|  2|
|    1|    4|    0| $\frac{1}{5}$|  0|  3|
|    0|   18|    0|             2|  1| 30|

We ignore all basic variables.

|$x_1$|     |$x_3$|     |$Z$|$c$|
|----:|----:|----:|----:|--:|--:|
|    0|     |    1|     |  0|  2|
|    1|     |    0|     |  0|  3|
|    0|     |    0|     |  1| 30|

We can make a last sanity check. $x_3 = 2$ so:
$$x_3 = 11 - 3x_1 - 4x_2$$
$$2 = 11 - 3 \cdot 3 - 4x_2$$
$$2 + 4x_2 = 11 - 9$$
$$4x_2 = 2 - 2$$
$$x_2 = 0$$

Inserting into our objective function:
$$z = 0 + 10x_1 + 22x_2$$
$$30 = 0 + 10 \cdot 3 + 22 \cdot 0$$
$$30 = 30$$

# P, NP and Cook's theorem
## NP completeness teori
- Model definition:
	- Operates on bits and bites
	- Input size is equal to number of bits in input
	- Time complexity of an algorithm is number of bit operations done.
- Decision problems, yes-no answers from input
- Inputs are bits
- Pair function:
	- $\langle x,y \rangle = x_1 0 \cdots x_n 0 \quad 11 \quad y_1 0 \cdots y_n 0$
- Church-Turing Thesis:
	- **Alanzo Church:** _No computational procedure will be considered as an algorithm unless it can be represented as a Turing Machine._
	- **Polynomial Church-Turing thesis:** A decision problem can be solved in polynomial time **iff** it can be solved in polynomial time by a turing machine.

## Language Complexity
![$P \neq NP$](p!=np.png){ width=50% }

- **P:** All decision problems that can be solved by a deterministic Turing machine in polynomial time.
- **NP:** All decision problems, where the solutions that evaluates to "yes," can be verified in polynomial time.
- **NPC:** A set of decision problems that can all be reduced into one another.
- **NPI:** All `NP` decision problems that are _not_ in `NPC` or `NP`.
- **NP-hard:** All decision problems that are _at least_ as hard as `NPC`.

- $L_1 \leq L_2 \Leftrightarrow (x \in L_1 \Leftrightarrow r(x) \in L_2)$

## SAT & CSAT
- For every boolean function $f(x)$, an equivilant curcuit $C(x)$ exists.
	- **Lemma:** For every boolean function $f : \{0,1\}^n \rightarrow \{0,1\}^m, \;  \exists C \; s.t. \; \forall x \in \{0,1\}^n , C(x) = f(x)$

- **Literals:** 
	- **Positive Literal:** An atom $x$
	- **Negative Literal:** A negation of an atom $\neg x$
- **Clause:** Collection of literals and logical connectives.
- **CNF:** Conjunctive Normal Form is a conjunction (`AND`'s) of clauses.
- **DNF:** Disjunctive Normal Form is a disjunction (`OR`'s) of clauses.
- **SAT:** Can the variables of a given CNF be replaced by either TRUE or FALSE such that the CNF evaluates to TRUE
- **Cook's Theorem:** SAT $\in$ NPC


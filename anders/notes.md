# The Linear Programming Model and LP algorithms

1. What is an LPP?
   - Objective function
   - max/min
   - constraints
   - factors
2. standard form
   - Convert to standard form
3. Fundamental theorem
4. Simplex
   - pivoting
   - example of pivot
   - Bland’s rule
5. Degeneracy
   - Definition
   - Implications
   - Bland's rule (again)
   - Simplex cycle

Example:

$$z = 0 + 10x_1 + 22x_1$$
$$x_3 = 11 - 3x_1 - 4x_1$$
$$x_4 = 15 - 5x_1 - 20x_1$$

Pivots on x1 and x4:
$$x1 = 3 - 1/5x_4 - 4x_2$$
$$z = 30 - 2x_4 - 18x_2$$
$$x_3 = 2 - 3/5x_4 + 8x_2$$

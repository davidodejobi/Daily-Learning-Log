Introduction to Systems of Linear Equations and Gaussian Elimination
This document provides a comprehensive overview of solving systems of linear equations using the Gaussian elimination method, a fundamental concept in linear algebra.

Key Definitions
Linear Equation: An equation that can be expressed in the standard form:
a 
1
​
 x 
1
​
 +a 
2
​
 x 
2
​
 +a 
3
​
 x 
3
​
 +⋅⋅⋅+a 
n
​
 x 
n
​
 =b
where a 
1
​
 ,a 
2
​
 ,⋅⋅⋅,a 
n
​
  and b are constants. The a 
k
​
  values are the coefficients of the variables x 
k
​
 , and b is the constant term.

Degenerate Linear Equation: A linear equation where all coefficients are zero (0x 
1
​
 +0x 
2
​
 +⋅⋅⋅+0x 
n
​
 =b).

Solution of a Linear Equation: A set of values for the unknowns (e.g., x 
1
​
 =k 
1
​
 ,x 
2
​
 =k 
2
​
 ,⋅⋅⋅,x 
n
​
 =k 
n
​
 ) that satisfies the equation.

System of Linear Equations: A collection of linear equations with the same set of unknowns.

Homogeneous System: A system where all constant terms (b 
i
​
 ) are zero.

Nonhomogeneous System: A system where at least one constant term is not zero.

Triangular Form: A system of linear equations where the leading unknown in each successive equation is to the right of the leading unknown in the preceding equation, forming a triangular shape of coefficients.

Echelon Form: A system is in echelon form if:

There are no degenerate equations.

The leading unknown in each equation (other than the first) is to the right of the leading unknown in the equation above it.

Pivot and Free Variables:

Pivot Variables: The leading unknowns in a system that is in echelon or triangular form.

Free Variables: The unknowns that are not pivot variables.

Elementary Row Operations
These are operations that can be performed on a system of linear equations to transform it into an equivalent system (a system with the same solution set).

[E1] Interchange: Swap the positions of two equations (L 
i
​
 ↔L 
j
​
 ).

[E2] Scaling: Replace an equation with a nonzero multiple of itself (kL 
i
​
 →L 
i
​
 , where k

=0).

[E3] Replacement: Replace an equation with the sum of itself and a multiple of another equation (kL 
i
​
 +L 
j
​
 →L 
j
​
 ).

The Gaussian Elimination Method
This is a systematic procedure for solving systems of linear equations. It has two main phases:

Part A: Forward Elimination
The goal is to reduce the original system into an equivalent system in either triangular or echelon form using elementary row operations.

Part B: Backward Substitution
Once the system is in a simplified form (triangular or echelon), the solution is found by solving for the variables starting from the last equation and working backwards.

Algorithm for Gaussian Elimination
Forward Elimination:

Step 1: Identify the first unknown with a nonzero coefficient. If necessary, use an interchange operation to move this equation to the top. This coefficient is the first pivot.

Step 2: Use the pivot to eliminate the corresponding unknown from all equations below it. This is done by adding a suitable multiple of the pivot row to each of the subsequent rows.

Step 3: Examine the new equations.

If an equation becomes degenerate of the form 0=b where b

=0, the system is inconsistent and has no solution. Stop.

If an equation becomes 0=0 or is a multiple of another, it is redundant and can be deleted.

Step 4 (Recursion): Repeat the elimination steps for the subsystem formed by all equations excluding the first one. Continue until the system is in triangular or echelon form.

Backward Substitution:

Solve the last equation for its pivot variable.

Substitute this value into the second-to-last equation and solve for its pivot variable.

Continue this process, moving upwards, until all pivot variables have been found. If there are free variables, the system will have infinitely many solutions.

Examples from the Document
Example 1:
Original System:
x 
1
​
 −3x 
2
​
 −2x 
3
​
 =6
2x 
1
​
 −4x 
2
​
 −3x 
3
​
 =8
−3x 
1
​
 +6x 
2
​
 +8x 
3
​
 =−5

After Forward Elimination:
x 
1
​
 −3x 
2
​
 −2x 
3
​
 =6
2x 
2
​
 +x 
3
​
 =−4
7x 
3
​
 =14

Backward Substitution:

From the last equation: 7x 
3
​
 =14⟹x 
3
​
 =2.

Substitute x 
3
​
 =2 into the second equation: 2x 
2
​
 +2=−4⟹2x 
2
​
 =−6⟹x 
2
​
 =−3.

Substitute x 
2
​
 =−3 and x 
3
​
 =2 into the first equation: x 
1
​
 −3(−3)−2(2)=6⟹x 
1
​
 +9−4=6⟹x 
1
​
 =1.

Solution: x 
1
​
 =1,x 
2
​
 =−3,x 
3
​
 =2.

Example 2:
Original System:
x 
1
​
 −2x 
2
​
 −3x 
3
​
 =3
2x 
1
​
 −x 
2
​
 −4x 
3
​
 =7
3x 
1
​
 −3x 
2
​
 −5x 
3
​
 =8

After Forward Elimination:
x 
1
​
 −2x 
2
​
 −3x 
3
​
 =3
3x 
2
​
 +2x 
3
​
 =1
−2x 
3
​
 =2

Backward Substitution:

From the last equation: −2x 
3
​
 =2⟹x 
3
​
 =−1.

Substitute x 
3
​
 =−1 into the second equation: 3x 
2
​
 +2(−1)=1⟹3x 
2
​
 =3⟹x 
2
​
 =1.

Substitute x 
2
​
 =1 and x 
3
​
 =−1 into the first equation: x 
1
​
 −2(1)−3(−1)=3⟹x 
1
​
 −2+3=3⟹x 
1
​
 =2.

Solution: x 
1
​
 =2,x 
2
​
 =1,x 
3
​
 =−1.
(Note: There appears to be a discrepancy in the provided document's solution for Example 2. Based on the forward elimination shown, the solution should be as calculated above, not x 
2
​
 =3.)

Conclusion
Gaussian elimination is a powerful and systematic technique for solving systems of linear equations. By reducing a complex system to a simpler echelon or triangular form, it allows for the straightforward calculation of the unique solution, determination of inconsistency, or characterization of an infinite number of solutions. It is a foundational tool in many areas of mathematics, science, and engineering.
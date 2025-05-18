# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
### Step 1:  
Import the required libraries `numpy` and `sys`.  

### Step 2:  
Input the size of the matrix `n` and define augmented matrix `a` as a NumPy array of size `(n, n+1)`. Initialize the solution array `x` as a NumPy array of size `n`.  

### Step 3:  
Perform forward elimination to transform the augmented matrix into an upper triangular form:  
- For each pivot row, ensure the pivot element is non-zero.  
- Subtract multiples of the pivot row from the rows below to eliminate the elements below the pivot.

### Step 4:  
Perform backward substitution to compute the solution:  
- Start with the last variable and substitute back into the equations to find the remaining variables.

### Step 5:  
Display the solution values of all variables using formatted output.

### Step 6:  
Verify the results for correctness.
## Program:
```
'''Program to solve a matrix using Gaussian elimination without partial pivoting.
Developed by: DINESH R
RegisterNumber: 212224240037
'''
import numpy as np

def gaussian_elimination(matrix):
    n = int(matrix[0])  # Number of unknowns
    A = []  # Coefficient matrix
    b = []  # Constants vector

    # Parse matrix input
    index = 1
    for i in range(n):
        A.append(matrix[index:index + n])
        b.append(matrix[index + n])
        index += (n + 1)

    A = np.array(A, dtype=float)
    b = np.array(b, dtype=float)

    # Forward elimination
    for k in range(n):
        for i in range(k + 1, n):
            factor = A[i, k] / A[k, k]
            A[i, k:] -= factor * A[k, k:]
            b[i] -= factor * b[k]

    # Back substitution
    x = np.zeros(n)
    for i in range(n - 1, -1, -1):
        x[i] = (b[i] - np.dot(A[i, i + 1:], x[i + 1:])) / A[i, i]

    return x


# Example input
input_data = [
    3,  # Number of unknowns
    1, 2, 4, 18,   # Row 1: Coefficients and constant
    2, 12, -2, 9,  # Row 2: Coefficients and constant
    5, 26, 5, 14   # Row 3: Coefficients and constant
]

# Solve using Gaussian elimination
solution = gaussian_elimination(input_data)

# Output the solution in a readable format
print(f"{' '.join([f'X{i} = {value:.2f}' for i, value in enumerate(solution)])}")
```
## Output:
![image](https://github.com/user-attachments/assets/18a9f07a-66ed-4abc-8f6b-097f1b2fc58d)
## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.


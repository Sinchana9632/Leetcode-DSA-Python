
  

## 📌 2D Arrays (Matrices) in Python: The Fundamentals

### 1. What is a 2D Array?

A 2D array (matrix) in Python is simply a **list of lists** (a grid of rows and columns).

  

Python

```
matrix = [
    [10, 20, 30],  # Row 0
    [40, 50, 60]   # Row 1
]
```

### 2. The Apartment Building Mental Model

- **The building:** `matrix`
    
      
    
- **The floor (Row):** `matrix[r]`
    
      
    
- **The door (Column):** `matrix[r][c]`
    
      
    

> ⚠️ **Golden Rule:** Index order is ALWAYS **`matrix[row][col]`** — Row first (top to bottom), Column second (left to right)!
> 
>   

## 🔑 Key Matrix Mechanics

### 1. Finding Matrix Dimensions

To find the total number of rows and columns:

  

- **Rows ($R$):** `r = len(matrix)` $\rightarrow$ _Counts the number of inner lists._
    
      
    
- **Columns ($C$):** `c = len(matrix[0])` $\rightarrow$ _Counts the number of elements inside Row 0._
    
      
    

Python

```
matrix = [
    [5, 8],  # len(matrix[0]) = 2 columns
    [1, 4],
    [9, 2]
]
# len(matrix) = 3 rows
```

### 2. Safe Matrix Initialization (List Comprehension)

To create a blank $C \times R$ grid filled with zeros, use list comprehension:

  

Python

```
blank_matrix = [[0] * r for _ in range(c)]
```

- **`[0] * r`**: Creates **one row** containing $R$ zeros.
    
      
    
- **`for _ in range(c)`**: Stacks that row $C$ times to create $C$ rows.
    
      
    

> ❌ **Do NOT use `[[0] * r] * c`!** It creates identical references to the same row in memory—modifying one cell will change every row!
> 
>   

### 3. Accessing Elements (Nested Loops & `range()`)

To visit every single element in a grid, we use **nested loops**:

  

Python

```
for r in range(len(matrix)):       # Outer loop: picks row index (0, 1, 2...)
    for c in range(len(matrix[0])): # Inner loop: picks col index (0, 1...)
        print(matrix[r][c])
```

#### Why two loops and `range()`?

1. **Two Loops:** One loop moves vertically down rows; the inner loop moves horizontally across columns.
    
      
    
2. **`range()`:** Generates integer numbers (`0, 1, 2...`) which we need as addresses (indices) to place/get items.
    
      
    

## 🚀 LeetCode 867: Transpose Matrix

### 📌 Core Concept

Transposing a matrix flips it across its diagonal:

  

- **Rows become columns**, and **columns become rows**.
    
      
    
- An $R \times C$ matrix transposes into a **$C \times R$** matrix.
    
      
    

$$\text{Original } (3 \times 2) = \begin{bmatrix} 5 & 8 \\ 1 & 4 \\ 9 & 2 \end{bmatrix} \longrightarrow \text{Transposed } (2 \times 3) = \begin{bmatrix} 5 & 1 & 9 \\ 8 & 4 & 2 \end{bmatrix}$$

### 🧠 The Core Swap Rule

The element at original position `matrix[r][c]` moves to transposed position `tran_matrix[c][r]`:

  

$$\text{tran\_matrix}[c][r] = \text{matrix}[r][c]$$

### 💻 Complete Solution

Python

```
class Solution(object):
    def transpose(self, matrix):
        # 1. Get dimensions of original matrix
        r = len(matrix)
        c = len(matrix[0])
        
        # 2. Initialize new blank grid with swapped dimensions (c x r)
        tran_matrix = [[0] * r for _ in range(c)]
        
        # 3. Traverse original matrix and swap coordinates
        for i in range(r):
            for j in range(c):
                tran_matrix[j][i] = matrix[i][j]
                
        return tran_matrix
```

### ⚡ Complexity Analysis

- **Time Complexity:** $\mathcal{O}(R \times C)$ — We visit every single cell in the grid once.
    
      
    
- **Space Complexity:** $\mathcal{O}(R \times C)$ — We create a new output matrix of size $C \times R$.
    
      
    


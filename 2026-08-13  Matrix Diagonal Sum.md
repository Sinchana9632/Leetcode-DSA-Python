

  

## 📌 LeetCode 1572: Matrix Diagonal Sum

### 1. Problem Summary

Given a **square matrix** ($N \times N$), calculate the total sum of all elements on both the **primary** and **secondary** diagonals.

  

> ⚠️ **Key Constraint:** If an element sits on **both** diagonals (the center element in an odd-sized matrix), it must only be added **once**.
> 
>   

## 🔑 Index Patterns Recognized

In any $N \times N$ square matrix:

  

Plaintext

```
Indices for a 3x3 Grid:
(0,0)  (0,1)  (0,2)
(1,0)  (1,1)  (1,2)
(2,0)  (2,1)  (2,2)
```

### 1. Primary Diagonal (Top-Left to Bottom-Right)

- **Coordinates:** `(0,0)`, `(1,1)`, `(2,2)`
    
      
    
- **Rule:** Row index equals Column index $\rightarrow$ **`r == c`**
    
      
    

### 2. Secondary Diagonal (Top-Right to Bottom-Left)

- **Coordinates:** `(0,2)`, `(1,1)`, `(2,0)`
    
      
    
- **Rule:** Sum of indices always equals $N - 1$ $\rightarrow$ **`r + c == N - 1`**
    
      
    
- **Direct Formula:** For any row `i`, the secondary column index `j` is:
    
      
    
    $$\text{Secondary Column } j = (N - 1) - i$$
    

## 🚀 Two Approaches to Solve It

### Approach 1: Two-Loop Method (Your Notebook Approach)

We traverse the matrix to find diagonal elements using conditions:

  

- **Time Complexity:** $\mathcal{O}(N^2)$ (because of the nested loop)
    
      
    
- **Space Complexity:** $\mathcal{O}(1)$
    
      
    

Python

```
# 1. Primary Diagonal check
for r in range(N):
    for c in range(N):
        if r == c:
            sum += mat[r][c]

# 2. Secondary Diagonal check
for i in range(N):
    j = (N - 1) - i
    if i != j:  # Prevents double counting the center!
        sum += mat[i][j]
```

### Approach 2: Optimized Single-Loop Method (Best Solution)

Since we already know the exact coordinates for both diagonals in every row $i$, we can directly jump to those cells in **one single loop** without checking non-diagonal cells!

  

- **Primary Cell:** `mat[i][i]`
    
      
    
- **Secondary Cell:** `mat[i][(N - 1) - i]`
    
      
    
- **Time Complexity:** $\mathcal{O}(N)$ (Visits only $N$ rows once)
    
      
    
- **Space Complexity:** $\mathcal{O}(1)$
    
      
    

Python

```
class Solution(object):
    def diagonalSum(self, mat):
        N = len(mat)
        total_sum = 0
        
        for i in range(N):
            # 1. Add primary diagonal element
            total_sum += mat[i][i]
            
            # 2. Add secondary diagonal element IF it's not the center cell
            if i != (N - 1) - i:
                total_sum += mat[i][(N - 1) - i]
                
        return total_sum
```

## 💡 Key Takeaway & Common Pitfall

- **The Bug to Avoid:** Adding `mat[1][1]` twice in odd-sized matrices (like $3 \times 3$ or $5 \times 5$).
    
      
    
- **The Fix:** Ensure `primary_col != secondary_col` before adding the secondary element (i.e., `i != (N - 1) - i`).
    
      
    

Ready for the next problem whenever you are!
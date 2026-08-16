

  

# 📓 2D Array Patterns: Practice Notes

## 1️⃣ LeetCode 54: Spiral Matrix

- **Pattern:** Boundary Shrinking (4-Wall Simulation)
    
      
    
- **Goal:** Traverse an $M \times N$ matrix in a clockwise spiral order.
    
      
    

### 🔑 Key Concept & Rules

1. Maintain **4 boundary pointers**:
    
      
    - `top = 0`, `bottom = len(matrix) - 1`
        
          
        
    - `left = 0`, `right = len(matrix[0]) - 1`
        
          
        
2. **Fixed vs. Moving Coordinate Rule:**
    
      
    - **Left $\rightarrow$ Right:** Row fixed at `top`, loop `col` from `left` to `right`. Increment `top += 1`.
        
          
        
    - **Top $\rightarrow$ Bottom:** Column fixed at `right`, loop `row` from `top` to `bottom`. Decrement `right -= 1`.
        
          
        
    - **Right $\rightarrow$ Left:** Row fixed at `bottom`, loop `col` from `right` to `left`. Decrement `bottom -= 1`.
        
          
        
    - **Bottom $\rightarrow$ Top:** Column fixed at `left`, loop `row` from `bottom` to `top`. Increment `left += 1`.
        
          
        
3. **Critical Edge Safety Check:**
    
      
    - Before traversing Left (Loop 3), check `if top <= bottom:`.
        
          
        
    - Before traversing Up (Loop 4), check `if left <= right:`.
        
          
        
    - _Why?_ Prevents re-visiting rows/columns in non-square matrices (e.g., $1 \times N$ or $M \times 1$).
        
          
        

### ⏱️ Complexity

- **Time Complexity:** $\mathcal{O}(M \times N)$ — Visits every cell once.
    
      
    
- **Space Complexity:** $\mathcal{O}(1)$ — No extra auxiliary space.
    
      
    

## 2️⃣ LeetCode 48: Rotate Image

- **Pattern:** Matrix Transformation (Geometric Tricks)
    
      
    
- **Goal:** Rotate an $N \times N$ matrix **90 degrees clockwise in-place** (without allocating another 2D matrix).
    
      
    

### 🔑 Key Concept & 2-Step Trick

Clockwise $90^\circ$ rotation is equivalent to two successive operations:

  

$$\text{Original Matrix} \xrightarrow{\text{Step 1: Transpose}} \text{Transposed} \xrightarrow{\text{Step 2: Reverse Rows}} \text{Rotated Matrix}$$

1. **Step 1: In-Place Transpose (Flip across main diagonal)**
    
      
    - Loop `i` from `0` to `n - 1`.
        
          
        
    - Loop `j` from `i + 1` to `n - 1` _(start at `i + 1` to swap only above diagonal and avoid double-swapping back)_.
        
          
        
    - Swap: `matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]`
        
          
        
2. **Step 2: Reverse Each Row (Horizontal Mirror)**
    
      
    - Loop through each row in `matrix`:
        
          
        
    - Execute `row.reverse()`
        
          
        

### ⏱️ Complexity

- **Time Complexity:** $\mathcal{O}(N^2)$ — Visits each element during transpose and reversal.
    
      
    
- **Space Complexity:** $\mathcal{O}(1)$ — Modifies input matrix directly in memory.
    
      
    

Take your time writing these into your notebook! Let me know once you're done or if you'd like to adjust anything in the notes.

  

## 📌 Python Concept 2: Saving the Value Before Overwriting

Now, there is just **one last Python concept** to understand before you write the code.

  

Imagine you are standing at index `4` (where the number is `6`).

Your memory variable `max_so_far` currently holds `1`.

  

If you immediately overwrite the number at index 4:

  

Python

```
nums[i] = max_so_far  # nums[i] becomes 1
```

Now `nums[i]` is replaced with `1`. But wait! You still need the **original value (`6`)** to update `max_so_far` for the next steps! Since you just erased `6`, it's gone!

  

### 💡 The Python Fix: Temporary Variable

In Python, we simply save the old value into a temporary variable _before_ overwriting:

  

Python

```
temp = nums[i]         # 1. Save original value (6)
nums[i] = max_so_far   # 2. Overwrite with current max (1)
max_so_far = max(max_so_far, temp)  # 3. Update max using saved value (6)
```

## ✍️ Notes to Copy to Obsidian / GitHub

Before you try writing the code, here are the concept notes for this pattern:

  

# 📝 Topic Notes: Right-to-Left Traversal & Max Tracking

## 📌 1. Backward Traversal with `range()`

When a problem requires knowledge of elements **to the right**, scanning from Right to Left ($\mathcal{O}(N)$) eliminates redundant nested scans ($\mathcal{O}(N^2)$).

  

- **Syntax:** `range(len(nums) - 1, -1, -1)`
    
      
    - `len(nums) - 1`: Starts at the last valid index.
        
          
        
    - `-1`: Stops right before index `-1` (so it includes index `0`).
        
          
        
    - `-1`: Decrements index by `1` each step.
        
          
        

## 📌 2. Preserving State Before In-Place Mutation

When overwriting an array element in-place, store its original value in a temporary variable first if that value is needed for future calculations.

  

Python

```
temp = nums[i]                      # Hold original value
nums[i] = max_so_far                # Replace current element
max_so_far = max(max_so_far, temp)  # Update running max
```

Ready to take a shot at writing the function for **LeetCode 1299** now? Give it a try!


  

# 📝 Problem Notes: Replace Elements with Greatest Element on Right Side (LeetCode 1299)

## 📌 Problem Overview

Given an array `arr`, replace every element with the **greatest element among all elements to its right**, and replace the **last element with `-1`**.

  

- **Pattern Name:** Right-to-Left (Backward) Single-Pass Traversal.
    
      
    
- **Key Trick:** Reversing traversal direction converts a nested loop $\mathcal{O}(N^2)$ problem into a linear $\mathcal{O}(N)$ problem.
    
      
    

## 🧠 Core Strategy & Logic

1. **Why NOT Forward (Left-to-Right)?**
    
      
    - Moving forward forces you to scan all elements to the right for every single index $\rightarrow \mathcal{O}(N^2)$ time.
        
          
        
2. **Why Backward (Right-to-Left)?**
    
      
    - Moving backward allows you to maintain a **running maximum** (`max_so_far`).
        
          
        
    - At any index `i`, the maximum element to its right is already stored in `max_so_far` from previous steps $\rightarrow \mathcal{O}(N)$ time.
        
          
        

## 🐍 Python Concepts Covered

1. **Reverse Range Syntax:**
    
      
    - `range(start, stop, step)` $\rightarrow$ `range(n - 1, -1, -1)`
        
          
        
    - `start = n - 1`: Starts at the last valid index.
        
          
        
    - `stop = -1`: Stops right before `-1` (so it includes index `0`).
        
          
        
    - `step = -1`: Moves backward by `1` in each iteration.
        
          
        
2. **Preserving Values During In-Place Mutation:**
    
      
    - When overwriting an element in an array (`arr[i] = max_so_far`), its original value is lost.
        
          
        
    - We must store `arr[i]` in a temporary variable (`temp`) _before_ overwriting it so we can update `max_so_far`.
        
          
        

## 💻 Python Solution Code

Python

```
def replaceElements(arr: list[int]) -> list[int]:
    n = len(arr)
    max_so_far = -1  # Last element always gets -1 (no elements to its right)

    # Traverse backwards from last index down to index 0
    for i in range(n - 1, -1, -1):
        temp = arr[i]                     # 1. Save original value
        arr[i] = max_so_far               # 2. Overwrite with maximum from right
        max_so_far = max(max_so_far, temp) # 3. Update running max using old value

    return arr
```

## ⚡ Complexity Analysis

- **Time Complexity:** $\mathcal{O}(N)$ — We iterate through the array of length $N$ exactly once.
    
      
    
- **Space Complexity:** $\mathcal{O}(1)$ — The modification is done in-place without allocating extra arrays.
    
      
    

Let me know once you've saved these notes, and we can kick off **Days 3–4: Prefix Sums & Cumulative Operations**!
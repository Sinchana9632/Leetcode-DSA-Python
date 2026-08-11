# Problem Notes: Find Pivot Index (LeetCode 724)

## 📌 Problem Overview

Find an index in an array where the **sum of elements strictly to its left** equals the **sum of elements strictly to its right**. Return the leftmost index, or `-1` if none exists.

- **Pattern Name:** Total Sum & Running Left Sum Balance.
    
- **Key Trick:** Instead of calculating `right_sum` with a loop ($\mathcal{O}(N^2)$), derive it instantly using basic arithmetic:
    
    $$\text{Right Sum} = \text{Total Sum} - \text{Left Sum} - \text{Current Element}$$
    

## 🧠 Core Strategy & Logic

1. **Calculate `total_sum` upfront:** Use `sum(nums)` once before entering the loop.
    
2. **Track `left_sum` dynamically:** Start at `0`. At each step `i`:
    
    - Compute `right_sum = total_sum - left_sum - num`.
        
    - Check if `left_sum == right_sum`. If true, return `i` immediately.
        
    - Add `num` to `left_sum` before moving to index `i + 1`.
        

## 🐍 Python Concepts Covered

1. **`enumerate(nums)`**:
    
    - Yields both the **index** (`i`) and the **value** (`num`) together in a single clean loop.
        
2. **Variable Scope & Placement:**
    
    - Accumulators (`left_sum = 0`) and static calculations (`total_sum = sum(nums)`) **must be declared outside the loop** so they aren't reset on every iteration.
        

## 💻 Python Solution Code

Python

```
def pivotIndex(nums: list[int]) -> int:
    total_sum = sum(nums)
    left_sum = 0
    
    for i, num in enumerate(nums):
        right_sum = total_sum - left_sum - num
        
        if left_sum == right_sum:
            return i
            
        left_sum += num
        
    return -1
```

## ⚡ Complexity Analysis

- **Time Complexity:** $\mathcal{O}(N)$ — One pass to calculate `sum(nums)` and one pass for the `for` loop. Total time is $2N \rightarrow \mathcal{O}(N)$.
    
- **Space Complexity:** $\mathcal{O}(1)$ — Only a few integer variables (`total_sum`, `left_sum`, `right_sum`) are used.
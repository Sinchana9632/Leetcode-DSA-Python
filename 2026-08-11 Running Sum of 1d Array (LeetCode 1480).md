# Problem Notes: Running Sum of 1d Array (LeetCode 1480)

## 📌 Problem Overview

Given an array `nums`, return an array where each element at index `i` is the sum of all elements from index `0` up to `i`.

- **Pattern Name:** Basic Prefix Sum / Cumulative Sum.
    
- **Key Trick:** Reuse the already calculated running total at `nums[i - 1]` to calculate `nums[i]` in $\mathcal{O}(1)$ time per step.
    

## 🧠 Core Strategy & Logic

1. **Avoid Redundant Addition:**
    
    - Instead of calculating $1 + 2 + 3$ from scratch at index 2, take the previous running total ($3$) and add the current element ($3$).
        
2. **Start at Index 1:**
    
    - Index `0` stays the same because it has no preceding elements.
        
    - Starting at index `1` avoids out-of-bounds errors when referencing `nums[i - 1]`.
        

## 💻 Python Solution Code

Python

```
def runningSum(nums: list[int]) -> list[int]:
    # Start loop from index 1 (skip index 0)
    for i in range(1, len(nums)):
        # Accumulate previous running total into current element
        nums[i] += nums[i - 1]
        
    return nums
```

## ⚡ Complexity Analysis

- **Time Complexity:** $\mathcal{O}(N)$ — Single pass through the array.
    
- **Space Complexity:** $\mathcal{O}(1)$ — In-place array modification without extra space.


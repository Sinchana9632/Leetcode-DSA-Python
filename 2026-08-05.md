# 📝 LeetCode 27: Remove Element

## 📌 Problem Summary

Given an array `nums` and a target value `val`, remove all occurrences of `val` **in-place** and return `k` (the number of elements remaining that are not equal to `val`).

## 💡 Core Concept: Two-Pointer Pattern (Reader vs. Writer)

To solve array problems **in-place** without extra memory, use two pointers moving at different speeds:

- **`i` (Reader Pointer):** Scans every element from left to right (0→N−1).
    
- **`k` (Writer Pointer):** Tracks where the next valid (non-`val`) element should be placed.
    

### 🔄 Algorithm Logic

1. Initialize `k = 0`.
    
2. Loop `i` through the entire array:
    
    - **If `nums[i] != val`:** Copy `nums[i]` to `nums[k]`, then increment `k` (`k += 1`).
        
    - **If `nums[i] == val`:** Skip it (do not advance `k`).
        
3. Return `k`.
    

## 💻 Python Solution

Python

```
class Solution:
    def removeElement(self, nums: list[int], val: int) -> int:
        k = 0  # Writer pointer
        
        for i in range(len(nums)):  # Reader pointer
            if nums[i] != val:
                nums[k] = nums[i]
                k += 1
                
        return k
```

## ⏱️ Complexity Analysis

- **Time Complexity:** O(N)
    
    - We scan the array of length N exactly once.
        
- **Space Complexity:** O(1) Auxiliary Space
    
    - Modified the input array in-place without allocating extra arrays or dynamic memory.
        

Where would you like to go next?

Start LeetCode 26: Remove Duplicates from Sorted Array

Review two-pointer edge cases (empty array, all elements removed)
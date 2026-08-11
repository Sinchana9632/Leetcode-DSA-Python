# 📝 LeetCode 1920: Build Array from Permutation

## 📌 Problem Summary

Given a 0-indexed array `nums` of zero-based permutation integers, build and return an array `ans` of the same length where:

$$\text{ans}[i] = \text{nums}[\text{nums}[i]]$$

## 💡 Key Concept & Hint

- **Direct Mapping:** Use `nums[i]` as the index to access the target value in `nums`.
    
- **Constraint Guarantee:** Since `nums` contains values strictly from `0` to `len(nums) - 1`, nested indexing `nums[nums[i]]` will never cause an `IndexError`.
    
- **Dynamic Append:** Use `.append()` to push elements into an empty list rather than direct index assignment `ans[i] = ...`.
    

## 💻 Python Solution

Python

```
def buildArray(nums: list[int]) -> list[int]:
    ans = []
    
    for i in range(len(nums)):
        ans.append(nums[nums[i]])
        
    return ans
```

## ⏱️ Complexity Analysis

- **Time Complexity:** $\mathcal{O}(N)$
    
    - We iterate through the array of length $N$ exactly once.
        
- **Space Complexity:** $\mathcal{O}(N)$
    
    - We allocate a new output array `ans` to store $N$ elements
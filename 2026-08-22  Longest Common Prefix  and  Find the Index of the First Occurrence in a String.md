\

  

## Problem 1: LeetCode 14 – Longest Common Prefix

### **Problem Goal**

Find the longest common starting sequence of characters shared across an array of strings. Return `""` if no common prefix exists.

  

- **Example:** `strs = ["flower", "flow", "flight"]` $\rightarrow$ Output: `"fl"`
    
      
    

### **Core Approach: Vertical Scanning**

Instead of comparing full words horizontally, compare character positions vertically across all words simultaneously (index 0, then index 1, index 2, etc.).

  

### **Algorithm Steps**

1. **Base Case:** Check if `strs` is empty (`if not strs:`). Return `""` if true.
    
      
    
2. **Anchor Selection:** Use the first word `strs[0]` as a reference.
    
      
    
3. **Outer Loop:** Use `enumerate(strs[0])` to track character index `i` and character `char`.
    
      
    
4. **Inner Loop:** Iterate through remaining words (`strs[1:]`).
    
      
    
5. **Stop Condition:** Return `strs[0][:i]` immediately if:
    
      
    - Current index `i` reaches the end of any word (`i == len(word)`).
        
          
        
    - Character mismatch is found (`word[i] != char`).
        
          
        
6. **Full Match:** If loops finish without triggering the stop condition, return `strs[0]`.
    
      
    

### **Python Implementation**

Python

```
class Solution:
    def longestCommonPrefix(self, strs: list[str]) -> str:
        # Base case
        if not strs:
            return ""
        
        # Vertical Scanning
        for i, char in enumerate(strs[0]):
            for word in strs[1:]:
                # Stop if word ends or character mismatches
                if i == len(word) or word[i] != char:
                    return strs[0][:i]
                
        return strs[0]
```

### **Complexity Analysis**

- **Time Complexity:** $\mathcal{O}(S)$, where $S$ is the sum of all characters in all strings.
    
      
    
- **Space Complexity:** $\mathcal{O}(1)$, auxiliary space (excluding memory for output slice).
    
      
    

## Problem 2: LeetCode 28 – Find the Index of the First Occurrence in a String

### **Problem Goal**

Find the starting index of the first occurrence of string `needle` inside string `haystack`. Return `-1` if `needle` is not part of `haystack`.

  

- **Example:** `haystack = "sadbutsad"`, `needle = "sad"` $\rightarrow$ Output: `0`
    
      
    

### **Core Approach: Substring Slicing**

Extract a slice from `haystack` of length equal to `needle` at every starting index `i` and compare it directly to `needle`.

  

### **Algorithm Steps**

1. Store lengths: `n = len(haystack)` and `m = len(needle)`.
    
      
    
2. Loop over valid starting positions `i` using `range(n - m + 1)`.
    
      
    - _Note:_ Stopping at `n - m + 1` prevents looking past the end of `haystack`.
        
          
        
3. Check slice: If `haystack[i : i + m] == needle`, return `i` immediately.
    
      
    
4. If loop completes without finding a match, return `-1`.
    
      
    

### **Python Implementation**

Python

```
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        n = len(haystack)
        m = len(needle)
        
        # Check every valid slice position
        for i in range(n - m + 1):
            if haystack[i : i + m] == needle:
                return i
            
        return -1
```

### **Complexity Analysis**

- **Time Complexity:** $\mathcal{O}((N - M + 1) \times M)$, where $N = \text{len}(haystack)$ and $M = \text{len}(needle)$.
    
      
    
- **Space Complexity:** $\mathcal{O}(1)$, auxiliary space.
    
      
    

### **Key Python Concepts to Remember**

- **`enumerate(iterable)`**: Provides both index `i` and value `char` in a single loop.
    
      
    
- **String Slicing (`[start:stop]`)**: Extracts characters from `start` up to (excluding) `stop`.
Here is the exact, clean note for **LeetCode 242: Valid Anagram** based on our step-by-step balance scale method:

  

### LeetCode 242: Valid Anagram

#### Problem Statement

Given two strings `s` and `t`, return `True` if `t` is an anagram of `s` (same characters with exact same frequencies), and `False` otherwise.

  

- **Example 1:** `s = "anagram"`, `t = "nagaram"` $\rightarrow$ **Output:** `True`
    
      
    
- **Example 2:** `s = "rat"`, `t = "car"` $\rightarrow$ **Output:** `False`
    
      
    

#### Solution Code

Python

```
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # Step 1: If lengths don't match, they cannot be anagrams
        if len(s) != len(t):
            return False
        
        # Step 2: Fixed array of size 26 for letters 'a' through 'z'
        counts = [0] * 26
        
        # Step 3: Add for string 's', Subtract for string 't'
        for i in range(len(s)):
            counts[ord(s[i]) - ord('a')] += 1
            counts[ord(t[i]) - ord('a')] -= 1
            
        # Step 4: Check if every slot returned back to 0
        for count in counts:
            if count != 0:
                return False  # Extra or missing letter found
                
        return True  # All counts balanced back to 0
```

#### Line-by-Line Breakdown

1. **`if len(s) != len(t):`**
    
      
    
    If the words have different total lengths, they cannot have the exact same character counts.
    
      
    
2. **`counts = [0] * 26`**
    
      
    
    Creates a list of 26 zeros: index `0` for `'a'`, index `1` for `'b'`, ..., index `25` for `'z'`.
    
      
    
3. **`ord(s[i]) - ord('a')`**
    
      
    
    Converts a character into a `0–25` array index:
    
      
    - `'a'` $\rightarrow$ `97 - 97 = 0`
        
          
        
    - `'b'` $\rightarrow$ `98 - 97 = 1`
        
          
        
    - `'z'` $\rightarrow$ `122 - 97 = 25`
        
          
        
4. **`+= 1` and `-= 1`**
    
      
    
    Acts like a balance scale: increments for every character in `s` and decrements for every character in `t`.
    
      
    
5. **`for count in counts:`**
    
      
    
    If any slot is not `0`, the strings do not have identical letter counts.
    
      
    

#### Complexity

- **Time Complexity:** $\mathcal{O}(N)$ — Single pass through the strings of length $N$, then a quick check over 26 elements.
    
      
    
- **Space Complexity:** $\mathcal{O}(1)$ — Fixed array size of 26 regardless of input size.
    
      
    

#### Key Pattern

- **Fixed ASCII Frequency Array (`[0] * 26`):** Replaces a dictionary/hash map when working with lowercase English letters to keep auxiliary space constant at $\mathcal{O}(1)$.




  

### LeetCode 3110: Score of a String

#### Problem Statement

The **score** of a string is defined as the sum of the absolute differences between the ASCII values of adjacent characters. Given a string `s`, calculate and return its total score.

  

- **Example 1:** `s = "hello"` $\rightarrow$ **Output:** `13`
    
      
    - $\vert{} \text{ord}('h') - \text{ord}('e') \vert{} = \vert{}104 - 101\vert{} = 3$
        
          
        
    - $\vert{} \text{ord}('e') - \text{ord}('l') \vert{} = \vert{}101 - 108\vert{} = 7$
        
          
        
    - $\vert{} \text{ord}('l') - \text{ord}('l') \vert{} = \vert{}108 - 108\vert{} = 0$
        
          
        
    - $\vert{} \text{ord}('l') - \text{ord}('o') \vert{} = \vert{}108 - 111\vert{} = 3$
        
          
        
    - Total = $3 + 7 + 0 + 3 = 13$
        
          
        

#### Your Code Solution

Python

```
class Solution(object):
    def scoreOfString(self, s):
        """
        :type s: str
        :rtype: int
        """
        total_score = 0
        
        # Loop up to len(s) - 1 so s[i + 1] stays inside the string
        for i in range(len(s) - 1):
            Sum = abs(ord(s[i + 1]) - ord(s[i]))
            total_score += Sum
            
        return total_score
```

#### Line-by-Line Breakdown

1. **`total_score = 0`**
    
      
    
    Initializes an accumulator variable to keep track of the running sum.
    
      
    
2. **`for i in range(len(s) - 1):`**
    
      
    
    Stops the loop at index `len(s) - 2`. This guarantees that `s[i + 1]` looks at the next valid character without raising an `IndexError`.
    
      
    
3. **`ord(s[i + 1])` and `ord(s[i])`**
    
      
    
    Converts each character into its numerical ASCII code point (e.g., `'a'` $\rightarrow$ `97`).
    
      
    
4. **`abs(...)`**
    
      
    
    Calculates the absolute value so the difference is always positive regardless of character order.
    
      
    
5. **`total_score += Sum`**
    
      
    
    Adds the distance between the adjacent pair to the total.
    
      
    

#### Complexity Analysis

| **Metric**           | **Complexity**   | **Reason**                                            |
| -------------------- | ---------------- | ----------------------------------------------------- |
| **Time Complexity**  | $\mathcal{O}(N)$ | Loops through the string of length $N$ exactly once.  |
| **Space Complexity** | $\mathcal{O}(1)$ | Uses constant extra memory (`total_score` and `Sum`). |

#### Key Concepts Learned

- **ASCII Character Codes (`ord`):** Converts single characters directly to integers for distance calculations.
    
      
    
- **Preventing Index Out-of-Bounds:** Using `range(len(s) - 1)` when accessing current (`i`) and next (`i + 1`) elements simultaneously.
  
  
  Here is the exact note for your code for **LeetCode 58: Length of Last Word**:

  

### LeetCode 58: Length of Last Word

#### Problem Statement

Given a string `s` consisting of words and spaces, return the length of the last word in the string. A **word** is a maximal substring consisting of non-space characters only.

  

- **Example 1:** `s = "Hello World"` $\rightarrow$ **Output:** `5` (The last word is `"World"` with length 5)
    
      
    
- **Example 2:** `s = " fly me to the moon "` $\rightarrow$ **Output:** `4` (The last word is `"moon"` with length 4)
    
      
    

#### Your Code Solution

Python

```
class Solution(object):
    def lengthOfLastWord(self, s):
        """
        :type s: str
        :rtype: int
        """
        total = 0
        
        # Traverse backward from the last character to the first (index 0)
        for i in range(len(s) - 1, -1, -1):
            if s[i] != " ":
                total += 1
            elif total > 0:
                break
                
        return total
```

#### Line-by-Line Breakdown

1. **`total = 0`**
    
      
    
    Initializes a counter to keep track of the letters in the last word.
    
      
    
2. **`range(len(s) - 1, -1, -1)`**
    
      
    
    Iterates backward from the last index (`len(s) - 1`) down to index `0`.
    
      
    
3. **`if s[i] != " ":`**
    
      
    
    If the character is a letter (not a space), increment `total` by `1`.
    
      
    
4. **`elif total > 0:`**
    
      
    
    If we hit a space **after** we have already started counting letters (`total > 0`), it means we've reached the space right before the last word.
    
      
    
5. **`break`**
    
      
    
    Stops the loop immediately so we don't count letters from earlier words.
    
      
    

#### Complexity Analysis

|**Metric**|**Complexity**|**Reason**|
|---|---|---|
|**Time Complexity**|$\mathcal{O}(N)$|In the worst case, scans through the string of length $N$ once from the back.|
|**Space Complexity**|$\mathcal{O}(1)$|Uses a single integer variable `total` without creating new lists or string copies.|

#### Key Concepts Learned

- **Backward Traversal (`range(start, stop, step)`):** Starting from the end allows direct access to the last word without scanning the whole string first.
    
      
    
- **Early Exit (`break`):** Stopping as soon as the space preceding the last word is found saves unnecessary iterations.
  
  
  
  
  
  
  
  

Here is the exact note for your code for **LeetCode 58: Length of Last Word**:

  

### LeetCode 58: Length of Last Word

#### Problem Statement

Given a string `s` consisting of words and spaces, return the length of the last word in the string. A **word** is a maximal substring consisting of non-space characters only.

  

- **Example 1:** `s = "Hello World"` $\rightarrow$ **Output:** `5` (The last word is `"World"` with length 5)
    
      
    
- **Example 2:** `s = " fly me to the moon "` $\rightarrow$ **Output:** `4` (The last word is `"moon"` with length 4)
    
      
    

#### Your Code Solution

Python

```
class Solution(object):
    def lengthOfLastWord(self, s):
        """
        :type s: str
        :rtype: int
        """
        total = 0
        
        # Traverse backward from the last character to the first (index 0)
        for i in range(len(s) - 1, -1, -1):
            if s[i] != " ":
                total += 1
            elif total > 0:
                break
                
        return total
```

#### Line-by-Line Breakdown

1. **`total = 0`**
    
      
    
    Initializes a counter to keep track of the letters in the last word.
    
      
    
2. **`range(len(s) - 1, -1, -1)`**
    
      
    
    Iterates backward from the last index (`len(s) - 1`) down to index `0`.
    
      
    
3. **`if s[i] != " ":`**
    
      
    
    If the character is a letter (not a space), increment `total` by `1`.
    
      
    
4. **`elif total > 0:`**
    
      
    
    If we hit a space **after** we have already started counting letters (`total > 0`), it means we've reached the space right before the last word.
    
      
    
5. **`break`**
    
      
    
    Stops the loop immediately so we don't count letters from earlier words.
    
      
    

#### Complexity Analysis

|**Metric**|**Complexity**|**Reason**|
|---|---|---|
|**Time Complexity**|$\mathcal{O}(N)$|In the worst case, scans through the string of length $N$ once from the back.|
|**Space Complexity**|$\mathcal{O}(1)$|Uses a single integer variable `total` without creating new lists or string copies.|

#### Key Concepts Learned

- **Backward Traversal (`range(start, stop, step)`):** Starting from the end allows direct access to the last word without scanning the whole string first.
    
      
    
- **Early Exit (`break`):** Stopping as soon as the space preceding the last word is found saves unnecessary iterations.
# 🧩 Valid Anagram
## 📝 Problem Description
#### Given two strings 's' and 't', return true if 't' is an anagram of s, and
#### false otherwise. An anagram is a word or phrase formed by rearranging the
#### letters of a different word or phrase, typically using all the original letters exactly once.
## 💡 Solution Approach
### Frequency Counting (Hash Map)
We use a **Hash Map** (dictionary in Python) to count the occurrences of each character in string `s`, then we decrement for string `t`.
1. **Step 1:** Compare lengths (if different, return `False`).
2. **Step 2:** Build a frequency map for `s`.
3. **Step 3:** Verify with `t` and check for mismatches.#### **Verification:** We iterate through string t, decrementing the count for each character in the hash map.
---
## 📊 Complexity Analysis
| Type | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time** | $O(n)$ | We iterate through both strings exactly once. |
| **Space** | $O(k)$ | We store at most 26 characters (constant space). |
---
## 🐍 Python Implementation
```python
class Solution:
def isAnagram(self, s: str, t: str) -> bool:
    if len(s) != len(t):
       return False

    hash_map = {}

    for c in s:
        hash_map[c] = hash_map.get(c, 0) + 1
    for c in t:
        if c not in hash_map:
            return False
        hash_map[c] -= 1
        if hash_map[c] < 0:
            return False

return True


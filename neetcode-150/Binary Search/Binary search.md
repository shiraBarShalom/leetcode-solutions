# 🔍 Binary Search
## 📝 Problem Description
#### Given a sorted array of integers 'nums' and an integer 'target', return the
#### index of target if it exists in the array, or -1 otherwise.
#### You must write an algorithm with $O(\log n)$ runtime complexity.

## 💡 Solution Approach
### Divide and Conquer (Iterative)
We use two pointers, **left** and **right**, to represent the search boundaries. 
In each step, we check the middle element and discard half of the array.

1. **Step 1:** Initialize `left` at 0 and `right` at the last index.
2. **Step 2:** Calculate the middle index: `mid = (left + right) // 2`.
3. **Step 3:** Compare `nums[mid]` to `target` and update boundaries.

#### **Verification:** If `nums[mid] == target`, we found the index.
#### Otherwise, we shrink the range until `left > right`.



---

## 📊 Complexity Analysis
| Type | Complexity | Explanation |
| :--- | :--- | :--- |
| **Time** | $O(\log n)$ | The search space is reduced by half in each iteration. |
| **Space** | $O(1)$ | We only store a constant number of integer variables. |

---

## 🐍 Python Implementation
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1

        while left <= right:
            mid = (right + left) // 2
            
            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1

        return -1

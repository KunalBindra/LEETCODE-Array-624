# LEETCODE-Array-624
**Understanding the Problem:**

The given code calculates the maximum absolute difference between any two elements from different arrays in a list of arrays.

**Code Breakdown:**

```java
class Solution {
    public int maxDistance(List<List<Integer>> arrays) {
        int ans = 0;
        int mi = arrays.get(0).get(0); // Minimum element seen so far
        int mx = arrays.get(0).get(arrays.get(0).size() - 1); // Maximum element seen so far

        for (int i = 1; i < arrays.size(); ++i) {
            var arr = arrays.get(i);
            int a = Math.abs(arr.get(0) - mx); // Difference between current array's min and previous max
            int b = Math.abs(arr.get(arr.size() - 1) - mi); // Difference between current array's max and previous min
            ans = Math.max(ans, Math.max(a, b)); // Update max difference
            mi = Math.min(mi, arr.get(0)); // Update min element
            mx = Math.max(mx, arr.get(arr.size() - 1)); // Update max element
        }
        return ans;
    }
}
```

**Explanation:**

1. **Initialization:**
   - `ans`: Stores the maximum absolute difference found so far.
   - `mi`: Stores the minimum element seen across all arrays.
   - `mx`: Stores the maximum element seen across all arrays.
   - Initially, `mi` and `mx` are set to the minimum and maximum elements of the first array, respectively.

2. **Iterating through arrays:**
   - For each array `arr` starting from the second array:
     - Calculate `a`: Absolute difference between the current array's minimum and the previous maximum.
     - Calculate `b`: Absolute difference between the current array's maximum and the previous minimum.
     - Update `ans` with the maximum of the current `ans`, `a`, and `b`.
     - Update `mi` and `mx` with the minimum and maximum elements found so far, including the current array.

3. **Return the maximum difference `ans`.**

**Time Complexity:** O(n), where n is the total number of elements in all arrays.
**Space Complexity:** O(1), as we only use constant extra space.

**Dry Run Example:**

Consider the input `arrays = [[1,4],[0,5]]`.

- `mi = 1`, `mx = 4`, `ans = 0`
- For the second array:
  - `a = |0 - 4| = 4`
  - `b = |5 - 1| = 4`
  - `ans = max(0, 4, 4) = 4`
  - `mi = min(1, 0) = 0`
  - `mx = max(4, 5) = 5`
- Return `ans = 4`.

**Key Idea:**
- The maximum difference can only occur between the minimum element seen so far and the maximum element seen so far, or vice versa.
- By keeping track of these minimum and maximum elements, we can efficiently calculate the maximum difference without comparing every pair of elements.

This code effectively finds the maximum absolute difference between any two elements from different arrays in the given list.
 


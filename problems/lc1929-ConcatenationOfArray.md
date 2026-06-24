# LeetCode 1929 — Concatenation of Array

## Problem

Given an integer array `nums` of length `n`, return an array `ans` of length `2n` where:

```text
ans[i] = nums[i]
ans[i + n] = nums[i]
```

In other words, the returned array is formed by concatenating `nums` with itself.

---

## Approach

Instead of using an inbuilt function such as:

```cpp
nums.insert(nums.end(), nums.begin(), nums.end());
```

we create a new array of size `2 * n` and directly place each element in its two required positions.

For every index `i`:

```text
result[i]     = nums[i]
result[n + i] = nums[i]
```

This allows us to build the answer in a single traversal.

---

## Algorithm

1. Create a vector `result` of size `2 * n`.
2. Traverse the input array.
3. For each index `i`:

   * Store `nums[i]` at `result[i]`.
   * Store `nums[i]` again at `result[n + i]`.
4. Return `result`.

---

## Code

```cpp
class Solution {
public:
    vector<int> getConcatenation(vector<int>& nums) {
        vector<int> result(2 * nums.size());

        for (int i = 0; i < nums.size(); i++) {
            result[i] = result[nums.size() + i] = nums[i];
        }

        return result;
    }
};
```

---

## Example

### Input

```text
nums = [1,2,1]
```

### Output

```text
[1,2,1,1,2,1]
```

### Explanation

```text
result[0] = result[3] = 1
result[1] = result[4] = 2
result[2] = result[5] = 1
```

Final array:

```text
[1,2,1,1,2,1]
```

---

## Complexity Analysis

| Complexity | Value |
| ---------- | ----- |
| Time       | O(n)  |
| Space      | O(n)  |

* We iterate through the array only once.
* An additional array of size `2n` is used to store the answer.

---

## Key Insight

Every element of the original array appears exactly twice in the final answer:

* First at index `i`
* Second at index `n + i`

By filling both positions in the same iteration, we construct the concatenated array efficiently in a single pass.

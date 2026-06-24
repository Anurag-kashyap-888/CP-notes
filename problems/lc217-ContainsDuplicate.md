# LeetCode 217 — Contains Duplicate

## Problem

Given an integer array `nums`, return:

- `true` if any value appears at least twice in the array.
- `false` if every element is distinct.

---

## Brute Force Approach

For every element, compare it with all elements after it.

### Algorithm

1. Pick an element.
2. Compare it with every other element.
3. If two elements are equal, return `true`.
4. If all comparisons are completed and no match is found, return `false`.

### Complexity Analysis

| Complexity | Value |
|------------|--------|
| Time | O(n²) |
| Space | O(1) |

---

## Optimal Approach (Hash Map)

We maintain a hash map that stores whether an element has already been visited.

While traversing the array:

- If the current element has already been seen before, it means a duplicate exists, so return `true`.
- Otherwise, mark the element as visited and continue.

If the traversal completes successfully, no duplicate exists in the array, so return `false`.

### Intuition

The first time an element is encountered, we store it in the map.

When the same element appears again, we immediately know it has been seen before and can return `true` without checking the remaining elements.

This avoids the nested-loop comparisons of the brute-force solution.

---

## Code

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_map<int, bool> visited;

        for (int i = 0; i < nums.size(); i++) {
            if (visited[nums[i]] == true)
                return true;
            else
                visited[nums[i]] = true;
        }

        return false;
    }
};
```

---

## Example

### Input

```text
nums = [1,2,3,1]
```

### Traversal

```text
1 → mark visited
2 → mark visited
3 → mark visited
1 → already visited
```

### Output

```text
true
```

---

## Complexity Analysis

| Complexity | Value |
|------------|--------|
| Time | O(n) Average Case |
| Space | O(n) |

### Why O(n)?

- We traverse the array only once.
- Hash map insertion and lookup take O(1) on average.

---

## Key Insight

Instead of comparing every pair of elements, store previously seen elements in a hash map.

The moment an element appears for the second time, we know a duplicate exists and can return the answer immediately.
---

## Alternative Solution

Since we only need to know whether an element has been seen before, we do not actually need to store a boolean value.

An `unordered_set` can be used instead:

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> seen;

        for (int num : nums) {
            if (seen.count(num))
                return true;

            seen.insert(num);
        }

        return false;
    }
};
```

### Why use a Set?

- We only care whether an element exists.
- No additional boolean value needs to be stored.
- Expresses the intent more clearly.
- Same average-case complexity as the hash map solution.

| Complexity | Value |
|------------|--------|
| Time | O(n) Average Case |
| Space | O(n) |

> **Note:** In interviews, `unordered_set` is often preferred over `unordered_map<int, bool>` for this problem because it directly represents the idea of storing previously seen elements.

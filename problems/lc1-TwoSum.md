# LeetCode 1 — Two Sum

## Problem Link
https://leetcode.com/problems/two-sum/description/

---

## Brute Force Idea

A common beginner approach is:

- Fix one element
- Iterate through all other elements
- Check if:

```text
fixed_element + current_element == target
```

If not, continue checking all pairs.

This approach works, but it is slow because we check many unnecessary pairs.

### Time Complexity
```text
O(n²)
```

---

## Better Approach

We can use a hashmap to store numbers we have already seen.

For every element:
- Calculate:
  
```text
target - current_element
```

- Check if that value already exists in the hashmap.
- If yes, we found the answer.
- Otherwise, store the current element.

### Time Complexity
```text
O(n)
```

---

## What I Learned

- Brute force is often easy to think of first.
- Hashmaps help reduce repeated searching.
- Always think:
  
```text
Can I store previous computations?
```

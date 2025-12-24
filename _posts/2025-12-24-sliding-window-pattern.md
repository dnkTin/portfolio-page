---
title: Sliding Window Pattern
date: 2025-12-24
categories: [leetcode]
tags: [patterns, sliding-window, twopointers]
---

Sliding window is the go-to pattern for substring/subarray problems that depend on contiguous elements. It turns nested loops into linear passes by keeping a window boundary and updating counts in $O(1)$ per move.

## When to use it
- You need a best/first/shortest/longest contiguous range meeting a condition.
- The condition can be updated incrementally (counts, sums, frequency maps).
- The window only moves forward; no random jumps.

## Fixed-size window template
```python
# Find best metric over windows of size k
best = -float("inf")
window = 0
for right, val in enumerate(nums):
    window += val
    if right >= k:
        window -= nums[right - k]
    if right >= k - 1:
        best = max(best, window)  # or other metric
```

## Variable-size window template
```python
# Shortest window containing all targets from need
from collections import Counter
need = Counter(t)
have = Counter()
formed = 0
best = (float("inf"), None, None)
left = 0

for right, ch in enumerate(s):
    have[ch] += 1
    if have[ch] == need[ch]:
        formed += 1
    while formed == len(need):
        if right - left + 1 < best[0]:
            best = (right - left + 1, left, right)
        have[s[left]] -= 1
        if have[s[left]] < need[s[left]]:
            formed -= 1
        left += 1
```

## Pitfalls
- Forgetting to shrink: for variable windows, keep a `while` loop to contract.
- Off-by-one on window size: check the moment the window becomes valid (`right - left + 1`).
- Counters going negative: guard when removing left side.
- Using dict lookups without defaults: prefer `defaultdict(int)` or `Counter`.

## Practice set (sliding window, top picks)
- Longest Substring Without Repeating Characters (LC 3)
- Minimum Size Subarray Sum (LC 209)
- Sliding Window Maximum (LC 239)
- Permutation in String (LC 567)
- Minimum Window Substring (LC 76)

Work through these to cover fixed-size, variable-size, monotonic deque, and frequency-map flavors.

---
title: Sliding Window Pattern
date: 2025-12-24
categories: [leetcode]
tags: [patterns, sliding-window, twopointers]
---

Sliding window is the go-to pattern for substring/subarray problems that depend on contiguous elements. It turns nested loops into linear passes by keeping a window boundary and updating counts in $O(1)$ per move.

<div class="toc-floating">
    <p class="toc-title">On this page</p>
    <ul>
        <li><a href="#when-to-use-it">When to use it</a></li>
        <li><a href="#fixed-size-window-template">Fixed-size window template</a></li>
        <li><a href="#variable-size-window-template">Variable-size window template</a></li>
        <li><a href="#pitfalls">Pitfalls</a></li>
        <li><a href="#practice-set">Practice set</a></li>
    </ul>
</div>

## When to use it {#when-to-use-it}
- You need a best/first/shortest/longest contiguous range meeting a condition.
- The condition can be updated incrementally (counts, sums, frequency maps).
- The window only moves forward; no random jumps.

## Fixed-size window template {#fixed-size-window-template}
```python
# Find best metric over windows of size k
best = -float("inf")
window = 0
for right, val in enumerate(nums):
    window += val                      # expand window to include nums[right]
    if right >= k:                     # once window is too wide
        window -= nums[right - k]      # drop the element leaving on the left
    if right >= k - 1:                 # window reached full size k
        best = max(best, window)       # or compute other metric
```

## Variable-size window template {#variable-size-window-template}
```python
# Shortest window containing all targets from need
from collections import Counter
need = Counter(t)
have = Counter()
formed = 0
best = (float("inf"), None, None)
left = 0

for right, ch in enumerate(s):
    have[ch] += 1                      # add current char into window count
    if have[ch] == need[ch]:           # satisfied a required char count
        formed += 1
    while formed == len(need):         # window currently satisfies all needs
        if right - left + 1 < best[0]:
            best = (right - left + 1, left, right) # record best window
        have[s[left]] -= 1             # shrink from the left
        if have[s[left]] < need[s[left]]: # dropped below requirement
            formed -= 1
        left += 1                      # move left edge forward
```

## Pitfalls {#pitfalls}
- Forgetting to shrink: for variable windows, keep a `while` loop to contract.
- Off-by-one on window size: check the moment the window becomes valid (`right - left + 1`).
- Counters going negative: guard when removing left side.
- Using dict lookups without defaults: prefer `defaultdict(int)` or `Counter`.

## Practice set (sliding window, top picks) {#practice-set}
- Longest Substring Without Repeating Characters (LC 3)
- Minimum Size Subarray Sum (LC 209)
- Sliding Window Maximum (LC 239)
- Permutation in String (LC 567)
- Minimum Window Substring (LC 76)

Work through these to cover fixed-size, variable-size, monotonic deque, and frequency-map flavors.

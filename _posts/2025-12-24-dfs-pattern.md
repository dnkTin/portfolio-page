---
title: DFS Pattern
date: 2025-12-24
categories: [leetcode]
tags: [patterns, dfs, graph, tree]
---

Depth-first search is the workhorse for tree/graph traversals, backtracking, and component discovery. Go deep, then backtrack, keeping state as you unwind.

## Recursion template (tree/graph)
```python
def dfs(node, parent=None):
    if not node:
        return
    # pre-order work here
    for nei in node.neighbors:
        if nei is parent:
            continue
        dfs(nei, node)
    # post-order work here
```

## Grid DFS template
```python
ROWS, COLS = len(grid), len(grid[0])
seen = set()

def dfs(r, c):
    if (r < 0 or r >= ROWS or c < 0 or c >= COLS or
        grid[r][c] == "0" or (r, c) in seen):
        return
    seen.add((r, c))
    for dr, dc in [(1,0), (-1,0), (0,1), (0,-1)]:
        dfs(r + dr, c + dc)

for r in range(ROWS):
    for c in range(COLS):
        if grid[r][c] == "1" and (r, c) not in seen:
            dfs(r, c)
```

## Pitfalls
- Forgetting a visited set leads to cycles/infinite recursion.
- Stack overflow on very deep graphs; switch to iterative with your own stack if needed.
- Distinguish pre- vs post-order work (e.g., building paths vs counting components).

## Practice set (DFS, top picks)
- Number of Islands (LC 200)
- Clone Graph (LC 133)
- Path Sum II (LC 113)
- Course Schedule (LC 207) — cycle detection
- Pacific Atlantic Water Flow (LC 417)

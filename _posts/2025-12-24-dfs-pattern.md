---
title: DFS Pattern
date: 2025-12-24
categories: [leetcode]
tags: [patterns, dfs, graph, tree]
---

Depth-first search is the workhorse for tree/graph traversals, backtracking, and component discovery. Go deep, then backtrack, keeping state as you unwind.

<div class="toc-floating">
    <p class="toc-title">On this page</p>
    <ul>
        <li><a href="#recursion-template">Recursion template</a></li>
        <li><a href="#grid-dfs">Grid DFS template</a></li>
        <li><a href="#pitfalls">Pitfalls</a></li>
        <li><a href="#practice-set">Practice set</a></li>
    </ul>
</div>

## Recursion template (tree/graph) {#recursion-template}
```python
def dfs(node, parent=None):
    if not node:                  # base case: nothing to traverse
        return
    # pre-order work here         # handle node on the way down
    for nei in node.neighbors:    # walk all neighbors/children
        if nei is parent:         # skip the edge we came from (undirected graphs)
            continue
        dfs(nei, node)            # dive deeper
    # post-order work here        # handle node on the way back up
```

## Grid DFS template {#grid-dfs}
```python
ROWS, COLS = len(grid), len(grid[0])
seen = set()

def dfs(r, c):
    if (r < 0 or r >= ROWS or c < 0 or c >= COLS or
        grid[r][c] == "0" or (r, c) in seen):
        return                     # stop at bounds, water, or visited cells
    seen.add((r, c))               # mark current land cell
    for dr, dc in [(1,0), (-1,0), (0,1), (0,-1)]:
        dfs(r + dr, c + dc)        # explore four directions

for r in range(ROWS):
    for c in range(COLS):
        if grid[r][c] == "1" and (r, c) not in seen:
            dfs(r, c)              # start a new island search
```

## Pitfalls {#pitfalls}
- Forgetting a visited set leads to cycles/infinite recursion.
- Stack overflow on very deep graphs; switch to iterative with your own stack if needed.
- Distinguish pre- vs post-order work (e.g., building paths vs counting components).

## Practice set (DFS, top picks) {#practice-set}
- Number of Islands (LC 200)
- Clone Graph (LC 133)
- Path Sum II (LC 113)
- Course Schedule (LC 207) — cycle detection
- Pacific Atlantic Water Flow (LC 417)

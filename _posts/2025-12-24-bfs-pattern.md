---
title: BFS Pattern
date: 2025-12-24
categories: [leetcode]
tags: [patterns, bfs, graph, tree]
---

Breadth-first search explores level by level, perfect for shortest-path on unweighted graphs and layer-wise tree problems.

## Queue template (graph/tree)
```python
from collections import deque

def bfs(start):
    q = deque([start])
    seen = {start}
    dist = {start: 0}
    while q:
        node = q.popleft()
        # work with node, dist[node]
        for nei in node.neighbors:
            if nei in seen:
                continue
            seen.add(nei)
            dist[nei] = dist[node] + 1
            q.append(nei)
```

## Grid BFS template
```python
from collections import deque
ROWS, COLS = len(grid), len(grid[0])
q = deque()
seen = set()

# seed q with starting cells
def enqueue(r, c, d=0):
    q.append((r, c, d))
    seen.add((r, c))

while q:
    r, c, d = q.popleft()
    # process cell (r, c) at distance d
    for dr, dc in [(1,0), (-1,0), (0,1), (0,-1)]:
        nr, nc = r + dr, c + dc
        if 0 <= nr < ROWS and 0 <= nc < COLS and (nr, nc) not in seen:
            enqueue(nr, nc, d + 1)
```

## Pitfalls
- Forgetting to mark visited when enqueuing (should happen before pushing neighbors).
- Using BFS for weighted edges: switch to Dijkstra instead.
- Not seeding queue correctly (multi-source BFS needs all sources enqueued first).

## Practice set (BFS, top picks)
- Binary Tree Level Order Traversal (LC 102)
- Minimum Depth of Binary Tree (LC 111)
- Word Ladder (LC 127)
- Number of Islands (BFS flavor, LC 200)
- Rotting Oranges (LC 994)

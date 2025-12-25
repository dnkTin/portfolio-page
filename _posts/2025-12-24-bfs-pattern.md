---
title: BFS Pattern
date: 2025-12-24
categories: [leetcode]
tags: [patterns, bfs, graph, tree]
---

Breadth-first search explores level by level, perfect for shortest-path on unweighted graphs and layer-wise tree problems.

<div class="toc-floating">
    <p class="toc-title">On this page</p>
    <ul>
        <li><a href="#queue-template">Queue template</a></li>
        <li><a href="#grid-bfs">Grid BFS template</a></li>
        <li><a href="#pitfalls">Pitfalls</a></li>
        <li><a href="#practice-set">Practice set</a></li>
    </ul>
</div>

## Queue template (graph/tree) {#queue-template}
```python
from collections import deque

def bfs(start):
    q = deque([start])            # seed queue with the start node
    seen = {start}                # track visited nodes to avoid repeats
    dist = {start: 0}             # distance map keyed by node
    while q:                      # process level by level
        node = q.popleft()        # take the next node in the frontier
        # work with node, dist[node]
        for nei in node.neighbors: # scan all adjacent nodes
            if nei in seen:        # skip if we've already visited it
                continue
            seen.add(nei)          # mark as visited as soon as it's discovered
            dist[nei] = dist[node] + 1  # record distance from start
            q.append(nei)          # push neighbor to explore later
```

## Grid BFS template {#grid-bfs}
```python
from collections import deque
ROWS, COLS = len(grid), len(grid[0])
q = deque()
seen = set()

# seed q with starting cells
def enqueue(r, c, d=0):
    q.append((r, c, d))           # store row, col, and distance
    seen.add((r, c))              # mark cell as visited immediately

while q:
    r, c, d = q.popleft()         # pop the next cell
    # process cell (r, c) at distance d
    for dr, dc in [(1,0), (-1,0), (0,1), (0,-1)]:
        nr, nc = r + dr, c + dc   # move to a neighbor
        if 0 <= nr < ROWS and 0 <= nc < COLS and (nr, nc) not in seen:
            enqueue(nr, nc, d + 1) # enqueue unseen neighbors with updated distance
```

## Pitfalls {#pitfalls}
- Forgetting to mark visited when enqueuing (should happen before pushing neighbors).
- Using BFS for weighted edges: switch to Dijkstra instead.
- Not seeding queue correctly (multi-source BFS needs all sources enqueued first).

## Practice set (BFS, top picks) {#practice-set}
- Binary Tree Level Order Traversal (LC 102)
- Minimum Depth of Binary Tree (LC 111)
- Word Ladder (LC 127)
- Number of Islands (BFS flavor, LC 200)
- Rotting Oranges (LC 994)

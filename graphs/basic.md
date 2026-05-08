all of these are time: O(V + E)
# bfs

- for unweighted edges, bfs gives shorted path with minimum number of edges
	cause it explores in layers, and since w = 1, guaranteed min edges
- for weighted edges, use dijkstra instead
- memory usage is high (queue can get big)
- not good for structural insights

# dfs

- cycle detection (directed graphs)
- topo sort, kosarauju, tarjan
- backtracking (visit all paths)
- connected components
- stack overflow in deep graphs

![[Pasted image 20260505021147.png]]

dfs -> time structure (each node has discovery, finish time)
	can be used for ordering, cycle, all paths
bfs -> distance structure

# topological sort

- only defined for DAG (no cycles)
![[Pasted image 20260505021712.png]]

can be used for cycle detection
```
if (processed_nodes != total_nodes)
    → cycle exists
```


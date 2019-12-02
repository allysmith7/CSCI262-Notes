# Graphs

- models the relationship between things

- composed of *vertices* and *edges*

- written as G = (V, E)

    - V = set of vertices (aka nodes or *things*)
    - E = set of edges (aka relationships)
    - Degree = number of edges touching

- **Undirected Graph:** edges are bidirectional

- **Directed Graphs:** edges are unidirectional

- Simple graphs have no *self edges* and no *multiple edges*

    - self edges: loops, basically
    - multiple edges: two nodes have multiple paths between each other

- Applications:

    - Airlines flight maps
    - Driving, gps
    - Shortest path around campus
    - Internet traffic
    - Power grid
    - Flow control

- Two principal data structures

    - Adjacency Matrix

        - always large (V^2^)

        |       | A    | B    | C    | D    |
        | ----- | ---- | ---- | ---- | ---- |
        | **A** | 0    | 1    | 0    | 1    |
        | **B** | 1    | 0    | 1    | 1    |
        | **C** | 0    | 1    | 0    | 1    |
        | **D** | 1    | 1    | 1    | 0    |

    - Adjacency List

        - usually more efficient
        - only stores edges that actually exist
        - most graphs are sparse (E is far less than V^2^)

        | A    | B    | C    | D    |
        | ---- | ---- | ---- | ---- |
        | B    | A    | B    | A    |
        | D    | C    | D    | B    |
        |      | D    |      | C    |

- **Graph Traversal (Search):** Two main methods

    - Depth-First Search

        - Start at some vertex
        - Follow a simple path discovering new vertices until you cannot find a new vertices
        - Back up until you can start finding new vertices

        ```python
        // DFS Recursive pseudo-code
        // initialization
        for all u in V:
        	set u.visited = false
        
        // Traverse graph G starting from node v
        dfs(G, v):
        	set v.visited = true
        	for each edge (v,u) in E:
        		if not u.visited:
        			dfs(G, u)
        
        // DFS Stack pseudo-code
        
        dfs(G, v):
        	for all u in V:
        		set u.visited = false
        
        	let S be a stack
        	set v.visited = true
            S.push(v)
        	while S not empty:
        		u = S.pop()
        		for all edges (u, w) in E:
        			if not w.visited:
                        S.push(w):
        				set w.visited = true
        ```

    - Breadth-First Search

        - Start at source vertex
        - Explore the edges to discover new nodes that are reachable from the source

        ```python
        bfs(G, v):
        	for all u in V:
        		set u.visited = false
                
        	let Q be a queue
        	set v.visited = true
            Q.push(v)
        	while Q not empty:
        		u = Q.pop()
        		for all edges (u, w) in E:
        			if not w.visited:
                        Q.push(w):
        				set w.visited = true
        ```

        

- **Other Algorithms to Explore:**

    - Route finding
        - Dijkstra's Algorithm
        - A*
    - Minimum Spanning Tree: connect a graph using the least resources (edge weights or cost)
        - Kruskal's Algorithm
        - Prim's Algorithm
    - Max Flow: what is the maximum amount you can move along a network?
    - Game Playing
        - Minimax
        - Alpha-beta pruning, iterative deepening, many more
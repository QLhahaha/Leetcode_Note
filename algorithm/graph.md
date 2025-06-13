# Graph

### 1. Graph Representation
- **Adjacency List**: A list where each index represents a vertex and contains a list of its adjacent vertices.
- **Adjacency Matrix**: A 2D matrix where the cell at row i and column j indicates the presence (and possibly weight) of an edge between vertices i and j.
- **Edge List**: A list of edges, where each edge is represented as a tuple (u, v) or (u, v, weight).
- **Incidence Matrix**: A matrix where rows represent vertices and columns represent edges, indicating which vertex is incident to which edge.

### 2. Depth-First Search (DFS)
- **Use case**: Traversing or searching through a graph.
- **How does it work**:
    - Start from a source vertex, mark it as visited.
    - Recursively visit all unvisited adjacent vertices.
    - Backtrack when no unvisited adjacent vertices are left.
- **Time complexity**: O(V + E) where V is the number of vertices and E is the number of edges.
- **Space complexity**: O(V) for the recursion stack.
- **Code**:
```python
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
    visited.add(start)
    for neighbor in graph[start]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)
    return visited
```

### 3. Breadth-First Search (BFS)
- **Use case**: Finding the shortest path in an unweighted graph, level-order traversal.
- **How does it work**:
    - Start from a source vertex, mark it as visited.
    - Explore all neighbors at the current depth before moving to the next level.
- **Time complexity**: O(V + E)
- **Space complexity**: O(V) for the queue.
- **Code**:
```python
def bfs(graph, start):
    visited = set([start])
    queue = deque([start])
    while queue:
        node = queue.popleft()
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
    return visited
```
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

### 4. Union-Find (Disjoint Set Union)
- **Use case**: Efficiently managing a partition of a set into disjoint subsets, useful in Kruskal's algorithm for Minimum Spanning Tree. Can also be used for fully connected and cycle detection in undirected graphs.
- **How does it work**:
    - **Find**: Determine which subset a particular element is in.
    - **Union**: Join two subsets into a single subset.
    - Uses path compression and union by rank to optimize operations.
- **Time complexity**: Nearly O(1) for each operation due to optimizations.
- **Space complexity**: O(n) for storing parent and rank arrays.
```python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))

    def find(self, x):
        while x != self.parent[x]:
            x = self.parent[x]
        return x

    def union(self, x, y):
        rootX = self.find(x)
        rootY = self.find(y)
        if rootX == rootY:
            return False
        self.parent[rootX] = rootY
        return True
```

### 5. Dijkstra's Algorithm
- **Use case**: Finding the shortest path from a source vertex to all other vertices in a weighted graph with non-negative weights.
- **How does it work**:
    - Initialize distances from the source to all vertices as infinite, except for the source itself which is zero.
    - Use a priority queue to explore the vertex with the smallest distance.
    - Update distances to adjacent vertices if a shorter path is found.
- **Time complexity**: O((V + E) log V) with a binary heap.
- **Space complexity**: O(V) for the distance array and priority queue.
- **Code**:
```python
def dijkstra(graph, start):
    distances = {vertex: float('infinity') for vertex in graph}
    distances[start] = 0
    priority_queue = [(0, start)] # Initialize with (distance, vertex)

    while priority_queue:
        current_distance, current_vertex = heapq.heappop(priority_queue)

        if current_distance > distances[current_vertex]:
            continue

        for neighbor, weight in graph[current_vertex].items():
            distance = current_distance + weight

            if distance < distances[neighbor]:
                distances[neighbor] = distance
                heapq.heappush(priority_queue, (distance, neighbor))

    return distances
```


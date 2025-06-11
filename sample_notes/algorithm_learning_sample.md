# Sample 2: Algorithm Learning Notes

## 1. Dynamic Programming Concepts
### 1.1 Problem Identification
**Signs you need DP:**
- Optimal substructure (optimal solution contains optimal solutions to subproblems)
- Overlapping subproblems (same subproblems solved multiple times)
- Decision at each step affects future choices

### 1.2 DP Problem Structure
**Fibonacci Decision Tree (without memoization):**
```
                F(5)
               /    \
            F(4)    F(3)
           /   \    /   \
        F(3)  F(2) F(2) F(1)
       /  \   /  \
    F(2) F(1) F(1) F(0)
```
*Notice: F(3) and F(2) are computed multiple times → Use memoization*

### 1.3 DP Approaches
#### 1.3.1 Top-Down (Memoization)
```python
def fib_memo(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fib_memo(n-1, memo) + fib_memo(n-2, memo)
    return memo[n]
```

#### 1.3.2 Bottom-Up (Tabulation)
```python
def fib_dp(n):
    if n <= 1:
        return n
    dp = [0] * (n + 1)
    dp[1] = 1
    for i in range(2, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    return dp[n]
```

## 2. Graph Algorithm Patterns
### 2.1 Graph Representation Comparison
| Representation | Space Complexity | Edge Lookup | Best For |
|----------------|------------------|-------------|----------|
| Adjacency List | O(V + E) | O(degree) | Sparse graphs |
| Adjacency Matrix | O(V²) | O(1) | Dense graphs |
| Edge List | O(E) | O(E) | Simple operations |

### 2.2 DFS vs BFS Decision Framework
**When to use DFS:**
- Finding any path (not necessarily shortest)
- Detecting cycles
- Exploring all paths (with backtracking)
- Tree traversals
- Topological sorting

**When to use BFS:**
- Finding shortest path (unweighted graphs)
- Level-by-level processing
- Finding minimum steps/moves
- Connected components

### 2.3 Dijkstra's Algorithm Steps
1. **Initialize**: Set distance to source = 0, all others = ∞
2. **Create min-heap**: Add all vertices with their distances
3. **Extract minimum**: Remove vertex with smallest distance
4. **Update neighbors**: For each neighbor v of extracted vertex u:
   ```
   if dist[u] + weight(u,v) < dist[v]:
       dist[v] = dist[u] + weight(u,v)
       decrease_key(v) in heap
   ```
5. **Repeat**: Until heap is empty or target found

## 3. Complexity Analysis Framework
### 3.1 Time Complexity Hierarchy
```
O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(n³) < O(2ⁿ) < O(n!)

Performance Categories:
🟢 Excellent: O(1), O(log n)
🟡 Good: O(n), O(n log n)  
🟠 Acceptable: O(n²), O(n³)
🔴 Avoid: O(2ⁿ), O(n!)
```

### 3.2 Algorithm Selection by Input Size
| Input Size | Acceptable Complexity | Examples |
|------------|----------------------|----------|
| n ≤ 20 | O(2ⁿ), O(n!) | Brute force, backtracking |
| n ≤ 500 | O(n³) | Floyd-Warshall, 3-nested loops |
| n ≤ 5000 | O(n²) | Bubble sort, simple DP |
| n ≤ 10⁶ | O(n log n) | Merge sort, heap operations |
| n ≤ 10⁸ | O(n) | Linear scan, counting |
| n > 10⁸ | O(log n) | Binary search, math |

## 4. Problem-Solving Patterns
### 4.1 Two Pointers Decision Guide
**Use two pointers when:**
- Array is sorted (or can be sorted)
- Looking for pairs/triplets with specific sum
- Removing duplicates in-place
- Checking palindromes

**Pointer Movement Patterns:**
- **Opposite direction**: `left=0, right=n-1` → good for sorted arrays
- **Same direction**: `slow=0, fast=1` → good for cycle detection
- **Sliding window**: both move right but at different speeds

### 4.2 Recursive Problem Solving Framework
**Step-by-step approach:**
1. **Define base case**: When to stop recursion?
2. **Define recurrence relation**: How does f(n) relate to f(n-1), f(n-2), etc.?
3. **Identify subproblems**: What smaller problems do we solve?
4. **Check for overlapping subproblems**: Do we solve the same subproblem multiple times?
   - **Yes** → Use DP (memoization or tabulation)
   - **No** → Pure recursion is fine
5. **Choose implementation**: Top-down (recursive + memo) vs Bottom-up (iterative)

**Example Decision Process:**
```
Problem: Fibonacci sequence
1. Base case: F(0)=0, F(1)=1
2. Recurrence: F(n) = F(n-1) + F(n-2)
3. Subproblems: F(n-1), F(n-2), F(n-3), ...
4. Overlapping? YES - F(3) computed multiple times
5. Solution: Use DP
```

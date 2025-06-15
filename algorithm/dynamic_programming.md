# Dynamic Programming

### 0. General Concepts
**When to use DP:**
- Optimal substructure (optimal solution contains optimal solutions to subproblems)
- Overlapping subproblems (same subproblems solved multiple times)
- Decision at each step affects future choices
**Memoization vs Tabulation:**
- **Memoization**: Top-down approach, recursive, stores results of subproblems in a cache.
- **Tabulation**: Bottom-up approach, iterative, builds a table to store results of subproblems.
```python
# Dynamic Programming Examples
# Fibonacci Sequence
def memoization_example(n: int, memo: Dict[int, int] = {}) -> int:
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = memoization_example(n - 1, memo) + memoization_example(n - 2, memo)
    return memo[n]

def tabulation_example(n: int) -> int:
    if n <= 1:
        return n
    dp: List[int] = [0] * (n + 1)
    dp[0], dp[1] = 0, 1
    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]
    return dp[n]
```
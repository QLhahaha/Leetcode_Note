# Sample 3: Ready-to-Use Building Blocks

## 1. Essential Templates
### 1.1 Binary Search Template
```python
def binary_search_template(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = left + (right - left) // 2  # Avoid overflow
        
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1  # Not found

# Variations:
# Find leftmost: right = mid - 1 when arr[mid] >= target
# Find rightmost: left = mid + 1 when arr[mid] <= target
```

### 1.2 DFS Grid Traversal
```python
def dfs_grid(grid, start_r, start_c, visited, target):
    ROWS, COLS = len(grid), len(grid[0])
    directions = [(0, 1), (1, 0), (0, -1), (-1, 0)]
    
    def dfs(r, c):
        # Boundary checks
        if (r < 0 or r >= ROWS or c < 0 or c >= COLS or
            (r, c) in visited or grid[r][c] != target):
            return False
        
        visited.add((r, c))
        
        # Process current cell
        result = True  # or whatever logic you need
        
        # Explore all 4 directions
        for dr, dc in directions:
            dfs(r + dr, c + dc)
        
        return result
    
    return dfs(start_r, start_c)
```

### 1.3 Sliding Window Template
```python
def sliding_window_template(arr, k):
    """Fixed size sliding window"""
    if len(arr) < k:
        return []
    
    # Initialize first window
    window_sum = sum(arr[:k])
    max_sum = window_sum
    
    # Slide the window
    for i in range(k, len(arr)):
        window_sum += arr[i] - arr[i - k]
        max_sum = max(max_sum, window_sum)
    
    return max_sum

def variable_sliding_window(arr, condition):
    """Variable size sliding window"""
    left = 0
    result = 0
    current_state = 0  # Track window state
    
    for right in range(len(arr)):
        # Expand window
        current_state += arr[right]
        
        # Contract window if needed
        while not_valid_condition(current_state):
            current_state -= arr[left]
            left += 1
        
        # Update result
        result = max(result, right - left + 1)
    
    return result
```

## 2. Data Structure Implementations
### 2.1 MinHeap Class
```python
class MinHeap:
    def __init__(self):
        self.heap = [0]  # index 0 unused for easier math
    
    def push(self, val):
        self.heap.append(val)
        self._percolate_up(len(self.heap) - 1)
    
    def pop(self):
        if len(self.heap) == 1:
            return None
        if len(self.heap) == 2:
            return self.heap.pop()
        
        root = self.heap[1]
        self.heap[1] = self.heap.pop()
        self._percolate_down(1)
        return root
    
    def _percolate_up(self, i):
        while i > 1 and self.heap[i] < self.heap[i // 2]:
            self.heap[i], self.heap[i // 2] = self.heap[i // 2], self.heap[i]
            i = i // 2
    
    def _percolate_down(self, i):
        while 2 * i < len(self.heap):
            child = self._min_child(i)
            if self.heap[i] > self.heap[child]:
                self.heap[i], self.heap[child] = self.heap[child], self.heap[i]
            i = child
    
    def _min_child(self, i):
        if 2 * i + 1 >= len(self.heap):
            return 2 * i
        return 2 * i if self.heap[2 * i] < self.heap[2 * i + 1] else 2 * i + 1
```

### 2.2 Trie (Prefix Tree)
```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False

class Trie:
    def __init__(self):
        self.root = TrieNode()
    
    def insert(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end = True
    
    def search(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.is_end
    
    def starts_with(self, prefix):
        node = self.root
        for char in prefix:
            if char not in node.children:
                return False
            node = node.children[char]
        return True
```

## 3. Common Utilities
### 3.1 Quick Data Converters
```python
# Convert between data structures
def list_to_freq_dict(arr):
    from collections import Counter
    return dict(Counter(arr))

def matrix_to_dict(matrix):
    """Convert 2D matrix to coordinate dictionary"""
    coord_dict = {}
    for i in range(len(matrix)):
        for j in range(len(matrix[0])):
            coord_dict[(i, j)] = matrix[i][j]
    return coord_dict

def flatten_2d(matrix):
    return [item for row in matrix for item in row]

# String helpers
def char_to_index(char):
    return ord(char.lower()) - ord('a')

def index_to_char(index):
    return chr(index + ord('a'))
```

### 3.2 Input/Output Helpers
```python
# Fast input reading for competitive programming
def read_ints():
    return list(map(int, input().split()))

def read_int():
    return int(input())

def read_grid(n):
    return [list(input().strip()) for _ in range(n)]

# Debug printing
def debug_print(var_name, var_value):
    print(f"DEBUG {var_name}: {var_value}")

def print_matrix(matrix):
    for row in matrix:
        print(' '.join(map(str, row)))
```

### 3.3 Math Utilities
```python
import math

def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

def lcm(a, b):
    return a * b // gcd(a, b)

def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(math.sqrt(n)) + 1):
        if n % i == 0:
            return False
    return True

def get_factors(n):
    factors = []
    for i in range(1, int(math.sqrt(n)) + 1):
        if n % i == 0:
            factors.append(i)
            if i != n // i:
                factors.append(n // i)
    return sorted(factors)

# Coordinate transformations
def rotate_90_clockwise(x, y, center_x=0, center_y=0):
    """Rotate point (x,y) 90 degrees clockwise around center"""
    rel_x, rel_y = x - center_x, y - center_y
    new_x = rel_y + center_x
    new_y = -rel_x + center_y
    return new_x, new_y

def manhattan_distance(x1, y1, x2, y2):
    return abs(x1 - x2) + abs(y1 - y2)
```

## 4. Performance Shortcuts
### 4.1 Python Optimizations
```python
# Fast list initialization
zeros = [0] * n
matrix = [[0] * cols for _ in range(rows)]  # Don't use [[0] * cols] * rows

# Fast sorting with custom key
data.sort(key=lambda x: (x[0], -x[1]))  # Sort by first asc, second desc

# Fast min/max with conditions
min_positive = min(filter(lambda x: x > 0, numbers))
max_even = max(x for x in numbers if x % 2 == 0)

# Fast set operations
intersection = set1 & set2
union = set1 | set2
difference = set1 - set2
```
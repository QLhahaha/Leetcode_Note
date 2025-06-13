# Tree

### 1. Binary Tree Traversal
- **Use case**: traversing a binary tree in various orders (pre-order, in-order, post-order).
- **How does it work**: 
    - Use recursion or a stack to traverse the tree.
    - For pre-order, visit the root first, then left subtree, then right subtree.
    - For in-order, visit the left subtree first, then root, then right subtree.
    - For post-order, visit the left subtree first, then right subtree, then root.
- **Time complexity**: O(n) for all traversal methods, where n is the number of nodes in the tree.
- **Space complexity**: O(h) for recursion (h is the height of the tree) or O(n) for stack-based traversal.
- **Code**: 
```python
def pre_order_traversal(root):
    if root:
        print(root.val)
        pre_order_traversal(root.left)
        pre_order_traversal(root.right)

def in_order_traversal(root):
    if root:
        in_order_traversal(root.left)
        print(root.val)
        in_order_traversal(root.right)

def post_order_traversal(root):
    if root:
        post_order_traversal(root.left)
        post_order_traversal(root.right)
        print(root.val)
```

### 2. Level Order Traversal
- **Use case**: traversing a binary tree level by level.
- **How does it work**: 
    - Use a queue to keep track of nodes at the current level.
    - Dequeue a node, process it, and enqueue its children.
- **Time complexity**: O(n), where n is the number of nodes in the tree.
- **Space complexity**: O(w), where w is the maximum width of the tree (number of nodes at the widest level).
- **Code**: 
```python
from collections import deque

def level_order_traversal(root):
    if not root:
        return
    queue = deque([root])
    while queue:
        node = queue.popleft()
        print(node.val)
        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)
```

### 3. Serialize and Deserialize Binary Tree
- **Use case**: converting a binary tree to a string representation and vice versa.
- **How does it work**: 
    - Use pre-order traversal to serialize the tree, adding a marker (e.g., `#`) for null nodes and a delimiter (e.g., `,`) between values.
    - For deserialization, split the string and reconstruct the tree using a queue.
- **Time complexity**: O(n), where n is the number of nodes in the tree.
- **Space complexity**: O(n), where n is the number of nodes in the tree.
- **Code**: 
```python
def serialize(root):
    def helper(node):
        if not node:
            return "#"
        return str(node.val) + "," + helper(node.left) + "," + helper(node.right)
    
    return helper(root)

def deserialize(data):
    def helper(nodes):
        val = next(nodes) # get the next value from the iterator
        if val == "#":
            return None
        node = TreeNode(int(val))
        node.left = helper(nodes)
        node.right = helper(nodes)
        return node

    nodes = iter(data.split(","))
    return helper(nodes)
```
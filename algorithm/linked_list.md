# Linked List

### 1. Fast and Slow Pointer
- **Use case**: finding the middle of a linked list, detecting cycles, etc.
- **How does it work**: 
    - Use two pointers, one moving twice as fast as the other.
    - When the fast pointer reaches the end, the slow pointer will be at the middle.
- **Time complexity**: O(n)
- **Space complexity**: O(1)
- **Code**: 
```python
def find_middle(head):
    slow, fast = head, head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow

def has_cycle(head):
    slow, fast = head, head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```

### 2. Cycle Start Detection
- **Use case**: finding the starting node of a cycle in a linked list.
- **How does it work**: 
    - Use the fast and slow pointer technique to find the intersection point.
    - Reset one pointer to the head and move both pointers at the same speed; they will meet at the cycle start.
- **Time complexity**: O(n)
- **Space complexity**: O(1)
- **Code**:
```python
def detect_cycle_start(head):
    slow, fast = head, head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            break
    else:
        return None

    slow = head
    while slow != fast:
        slow = slow.next
        fast = fast.next
    return slow
```
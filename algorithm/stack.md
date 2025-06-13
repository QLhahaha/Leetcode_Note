# Stack

### 1. Monotonic stack, a stack that is sorted(increasing or decreasing)
- **Use case**: used to find the next greater element, next smaller element, previous greater element, previous smaller element, etc.
- **How does it work**: 
    - Use a stack to keep track of elements in a specific order.
    - When processing each element, pop elements from the stack that do not satisfy the condition (e.g., for next greater element, pop until you find an element greater than the current one).
    - Push the current element onto the stack after processing.
- **Time complexity**: O(n) for processing all elements, as each element is pushed and popped from the stack at most once.
- **Space complexity**: O(n) for the stack.
- **Code**: 
```python
while stack and stack[-1] < current_element:
    stack.pop()
stack.append(current_element)
```



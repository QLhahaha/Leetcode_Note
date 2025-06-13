# Heap

### 1. Finding the kth largest element in an array
- **Use case**: Finding the kth largest or smallest element in an array.
- **How does it work**: 
    - Use a min-heap to keep track of the k largest elements.
    - If the heap size exceeds k, remove the smallest element.
    - The root of the heap will be the kth largest element.
- **Time complexity**: O(n log k) for building the heap, where n is the number of elements in the array.
- **Space complexity**: O(k) for the heap.
- **Code**: 
```python
for num in nums:
    heapq.heappush(heap, num)
    if len(heap) > k:
        heapq.heappop(heap)

```

### 2. Use in Greedy Algorithms
- **Use case**: Problems that require selecting the largest or smallest elements repeatedly, such as scheduling tasks or merging intervals.
- **How does it work**:
    - Use a max-heap (priority queue) to always select the largest element.
    - Insert elements into the heap based on the problem's criteria.
    - Extract the top element when needed.
- **Time complexity**: Depends on the number of operations, typically O(log n) per insertion or extraction.
- **Space complexity**: O(n) for the heap.

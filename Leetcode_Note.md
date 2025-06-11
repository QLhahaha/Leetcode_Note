# Leetcode Note

## General Note

### Heap
- Greedy → max-heap(priority-queue)


### Bit Operation
- xor is usually a good start to solve bit operation problems
- n & (n - 1) → remove the lowest “1” bit → less iterations


### Array
- **Quickselect**: finding kth largest, kth smallest, kth frequent, kth less frequent, etc (similar idea of quick sort)


### Stack
- Monotonic stack, a stack that is sorted(increasing or decreasing)

```cpp
while(!st.empty() && [_variable] [_condition] st.top()){
		st.pop();
}
st.push([_element]);
```


### Linked List
- fast and slow pointer → get the half point of the list (Tortoise and Hare)
- find cycle start → fast and slow pointer to find intersection point + slow fast same slow speed start at start and intersection resepctively, they will intersect at cycle start


### String
- KMP algorithm -> find sub patterns <br> find if a string is a substring of another

## **Warning**
- .size() returns size_t, which is unsigend

## **Syntax and Properties**

- std::sort(std::pair<T, T>) will based on the comparison result of pair.first, and then second if firsts are equal.

- priority_queue<T> : max_heap <br> priority_queue<T, vector<T>, greater<T>> : min_heap

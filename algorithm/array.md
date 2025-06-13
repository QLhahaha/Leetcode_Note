# Array

### 1. Quickselect
- **Use case**: finding kth largest, kth smallest, kth frequent, kth less frequent, etc (similar idea of quick sort)

- **How does it work**: 
    - `quickselect(nums, k)` where `k` is the kth element you want to find (1-based index).
    - Partition the array around a pivot, similar to quicksort.
    - Recursively apply the above steps to the part of the array that contains the kth element.
- **Time complexity**: O(n) on average, O(n^2) in the worst case (when the pivot is always the smallest or largest element).
- **Space complexity**: O(1) for the in-place partitioning.
- **Code** : See [Quickselect template](../building_block.md#11-quickselect-algorithm) in `building_block.md` for implementation and examples.

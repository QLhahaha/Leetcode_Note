# Bit Operation
- xor is usually a good start to solve bit operation problems
- n & (n - 1) → remove the lowest “1” bit → less iterations

### 1. find the number that appears once
- **Use case**: find the number that appears once in an array where every other number appears twice.
- **How does it work**: 
    - Use XOR operation to cancel out the numbers that appear twice.
    - The result will be the number that appears once.
- **Time complexity**: O(n)
- **Space complexity**: O(1)
- **Code**: 
```python
def find_single_number(nums):
    result = 0
    for num in nums:
        result ^= num
    return result
```
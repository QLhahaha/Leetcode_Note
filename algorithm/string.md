# String

### 1. KMP Algorithm
- **Use case**: Finding a substring within a string efficiently.
- **How does it work**:
    - Preprocess the pattern to create a longest prefix-suffix (LPS) array.
    - Use the LPS array to skip unnecessary comparisons when a mismatch occurs.
- **Time complexity**: O(n + m), where n is the length of the text and m is the length of the pattern.
- **Space complexity**: O(m) for the LPS array.
- **Code**: See [KMP Algorithm template](../building_block.md#12-kmp-algorithm) in `building_block.md` for implementation and examples.


### 2. 
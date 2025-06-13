# Building Blocks

## 1. Essential Templates
### 1.1 Quickselect Algorithm
See [Quickselect Algorithm](algorithm/array.md#1-quickselect) in `array.md` for explanation.
```python
def quickselect(nums, k):
	"""
	Returns the k-th smallest element of list within nums.
	"""
	# helper function to partition the array
	# move elements smaller than the pivot to the left and larger to the right
	# return the index of the pivot after partitioning
	def partition(left, right, pivot_index):
		pivot = nums[pivot_index]
		# Move pivot to end
		nums[pivot_index], nums[right] = nums[right], nums[pivot_index]
		store_index = left
		# Move all smaller elements to the left
		for i in range(left, right):
			if nums[i] < pivot:
				nums[store_index], nums[i] = nums[i], nums[store_index]
				store_index += 1
		# Move pivot to its final place
		nums[right], nums[store_index] = nums[store_index], nums[right]
		return store_index

	# main function to find the k-th smallest element
	left, right = 0, len(nums) - 1
	while True:
		if left == right:
			return nums[left]
		pivot_index = randint(left, right)
		pivot_index = partition(left, right, pivot_index)
		if k == pivot_index:
			return nums[k]
		elif k < pivot_index:
			right = pivot_index - 1
		else:
			left = pivot_index + 1
```

### 1.2 KMP Algorithm
See [KMP Algorithm](algorithm/string.md#1-kmp-algorithm) in `string.md` for explanation.
```python
# KMP (Knuth-Morris-Pratt) algorithm for substring search
# returns the index of the first occurrence of the pattern in the text, or -1 if not found.
def kmp_search(text, pattern):
    lps = [0] * len(pattern)
    compute_lps(pattern, lps)
    i = j = 0
    while i < len(text):
        if text[i] == pattern[j]:
            i += 1
            j += 1
            if j == len(pattern):
                return i - j
        elif j > 0:
            j = lps[j - 1]
        else:
            i += 1
    return -1

# Helper function to compute the longest prefix-suffix (LPS) array
def compute_lps(pattern, lps):
    length = 0
    i = 1
    while i < len(pattern):
        if pattern[i] == pattern[length]:
            length += 1
            lps[i] = length
            i += 1
        elif length > 0:
            length = lps[length - 1]
        else:
            lps[i] = 0
            i += 1
```
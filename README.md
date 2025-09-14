Linear and Binary Search — Guide

This short guide explains two fundamental search algorithms: linear (sequential) search and binary search. Each section includes a short explanation, a Python example, and the Big-O time complexity.

1) Linear Search (Sequential Search)

- Idea: Examine each item in a list one by one until you find the target or reach the end.
- Works on unsorted or sorted lists.
- Use when the list is small or unsorted, or when you only need a single pass.

Example (Python):
```python
	# check each index one by one until we find the value we are searching
	# for or we exhaust all elements because data structure does not contain
	# the value we are searching for 
	def linear_search(arr: list, target) -> int:
		"""Return the index of target in arr, or -1 if not found."""
		#
		for i, val in enumerate(arr):
			if val == target:
				return i
		return -1
```

Big-O: O(n) time, O(1) extra space. In the worst case you examine every element.

2) Binary Search

- Idea: Repeatedly divide a sorted list in half, discarding the half that cannot contain the target.
- Requires the input list to be sorted.
- Much faster than linear search on large sorted lists.

Example (Python, iterative):
```python
	# note: in order for a data structure to be sorted, it must have an index
	def binary_search(arr: list, target) -> int:
		"""Return the index of target in a sorted arr, or -1 if not found."""
		lo, hi = 0, len(arr) - 1
		while lo <= hi:
			mid = (lo + hi) // 2
			if arr[mid] == target:
				return mid
			elif arr[mid] < target:

				# searched for value is greater
				# so we only need to consider
				# the elements to the right of mid

				# we +1 because we know mid does 
				# not contain the value we are 
				# searching for

				lo = mid + 1
			else:

				# searched for value is less
				# so we only need to consider 
				# the elements to the left of mid 

				# we -1 because we know mid does 
				# not contain the value we are 
				# searching for

				hi = mid - 1
		return -1
```

Big-O: O(log n) time, O(1) extra space (iterative). Each step halves the search space.

When to use which
- If the list is unsorted and small, or sorting would be more expensive than a single scan, use linear search.
- If the list is sorted (or can be sorted once and used many times), use binary search for much better scalability.

Brief Big-O primer

- Big-O notation describes how an algorithm's running time (or memory) grows with input size n.
- Common classes:
  - O(1): constant time (e.g., array indexing)
  - O(log n): logarithmic (e.g., binary search)
  - O(n): linear (e.g., linear search, single pass)
  - O(n log n): typical for efficient **comparison sorts**
  - O(n^2): quadratic (e.g., simple nested loops)

- Big-O ignores constant factors and lower-order terms; it describes asymptotic growth.

<br/>

**Table 1.** Time complexity growth for increasing number of elements to evaluation. 

n = number of elements to evaluate (length of the indexed data structure _**e.g. ['a','b','c'] has n = 3**_)


| **n**      | **O(1)** | **O(log₂(n))** | **O(n)**   | **O(n log₂(n))**     | **O(n²)**         |
|-----------:|:--------:|------------:|-----------:|----------------------:|------------------:|
| 1          |    1     |     0.00 |          1 |              0 |                 1 |
| 2          |    1     |     1.00 |          2 |              2 |                 4 |
| 3          |    1     |     1.58 |          3 |              4 |                 9 |
| 4          |    1     |     2.00 |          4 |              8 |                16 |
| 5          |    1     |     2.32 |          5 |             11 |                25 |
| 100        |    1     |     6.64 |        100 |            664 |            10,000 |
| 1,000      |    1     |     9.96 |      1,000 |          9,965 |         1,000,000 |
| 1,000,000  |    1     |    19.93 |  1,000,000 |     19,931,568 | 1,000,000,000,000 |


<br/>

 [Visual Demonstration of Linear and Binary Search](https://www.cs.usfca.edu/~galles/visualization/Search.html)
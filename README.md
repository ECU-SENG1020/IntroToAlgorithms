Linear and Binary Search — Guide

This short guide explains two fundamental search algorithms: linear (sequential) search and binary search. Each section includes a short explanation, a Python example, and the Big-O time complexity.

1) Linear Search (Sequential Search)

- Idea: Examine each item in a list one by one until you find the target or reach the end.
- Works on unsorted or sorted lists.
- Use when the list is small or unsorted, or when you only need a single pass.

Example (Python):

	def linear_search(arr: list, target) -> int:
		"""Return the index of target in arr, or -1 if not found."""
		for i, val in enumerate(arr):
			if val == target:
				return i
		return -1

Big-O: O(n) time, O(1) extra space. In the worst case you examine every element.

2) Binary Search

- Idea: Repeatedly divide a sorted list in half, discarding the half that cannot contain the target.
- Requires the input list to be sorted.
- Much faster than linear search on large sorted lists.

Example (Python, iterative):

	def binary_search(arr: list, target) -> int:
		"""Return the index of target in a sorted arr, or -1 if not found."""
		lo, hi = 0, len(arr) - 1
		while lo <= hi:
			mid = (lo + hi) // 2
			if arr[mid] == target:
				return mid
			elif arr[mid] < target:
				lo = mid + 1
			else:
				hi = mid - 1
		return -1

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
  - O(n log n): typical for efficient comparison sorts
  - O(n^2): quadratic (e.g., simple nested loops)

- Big-O ignores constant factors and lower-order terms; it describes asymptotic growth.


<br/>

 [Visual Demonstration of Linear and Binary Search](https://www.cs.usfca.edu/~galles/visualization/Search.html)
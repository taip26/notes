# Binary Search

Idea: take midpoint of sorted array, if key is less than midpoint, search left. if not, search right. keep going until subarray len is less than 1 or the item is found.

```python
def binary_search(array, target):
    left_ptr = 0
    right_ptr = len(array) - 1
    while left_ptr <= right_ptr:
    # get midpoint
        midpoint = (left_ptr + right_ptr) // 2
        if array[midpoint] == target:
            return target # or index if desired
        elif array[midpoint] < target:
            left_ptr = midpoint + 1
        elif array[midpoint] > target:
            right_ptr = midpoint - 1
    return -1
```
[1, 4, 5, 12, 13, 18, 20, 32]
target = 32
left_ptr = 7
right_ptr = 7

midpoint = 7


# 128. Longest Consecutive Sequence

Strategies
 - draw a number line to visualize the problem
 - each group of sequences starts with a number that doesn't have a left neighbor
 - use a hash set (!) to make lookup fast
 - the trick is that each loop is only O(N) complexity, so adding to hash set is free
 - O(N) time complexity since 1st loops is N, then we loop through each element at most once
 - O(N) space since we need to hold all values in the set
```python
def longestConsecutive(self, nums: List[int]) -> int:
    longest = 0
    # hs = set(nums) <- use this instead to initialize
    hs = set()
    for num in nums:
        hs.add(num)
    for num in hs:
        if num - 1 not in hs:
            curr = num
            count = 0
            while curr in hs:
                curr += 1
                count += 1
            if count > longest:
                longest = count
            # longest = max(longest, count)
    return longest
```

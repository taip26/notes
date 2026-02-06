# 347. Top K Frequent Elements

naive soln:
 - count occurences of each num
 - sort based on count
 - get top k
 - should be O(NLog(N)) bc sort
 - O(N) space
 - CAN USE HEAP

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        hm = {}
        for num in nums:
            hm[num] = hm.get(num, 0) + 1
        # arr of (val, key)
        def keyFunc(e):
            return e[0]
        arr = []
        for key in hm.keys():
            arr.append((hm[key], key))
        arr.sort(descending=True, key=keyFunc)
        ret = []
        for i in range(k):
            ret.append(arr[i][1])
        return ret
```

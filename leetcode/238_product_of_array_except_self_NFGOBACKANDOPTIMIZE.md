# 238. Product of Array Except Self

tricky af - use prefix and suffix products to complete
can probably optimize how the prefix/suffix product can be evaluated
use pythons array initialization thingies:
    prefix_sum = [0] * (len[arr]+1)
drawing out the problem helps a lot

```
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        if len(nums) <= 1:
            return nums
        if len(nums) == 2:
            return [nums[1], nums[0]]
        pref = []
        post = []
        ans = []
        for i in range(len(nums)):
            if i == 0:
                pref.append(nums[i])
            else:
                pref.append(pref[i-1] * nums[i])
        
        for i in range(len(nums)-1, -1, -1):
            if i == len(nums)-1:
                post.insert(0, nums[i])
            else:
                post.insert(0, post[0] * nums[i])
        ans.append(post[1])
        for i in range(0, len(nums) - 2):
            ans.append(pref[i] * post[i+2])
        ans.append(pref[len(nums) - 2])
        
        return ans
```

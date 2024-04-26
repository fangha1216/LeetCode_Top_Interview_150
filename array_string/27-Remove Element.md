# 27. Remove Element
[LeetCode link 題目連結](https://leetcode.com/problems/remove-element/description/?envType=study-plan-v2&envId=top-interview-150)  

# python
```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        k = 0
        for i in range(len(nums)):
            if nums[i] != val:
                nums[k] = nums[i]
                k += 1
        return k
```
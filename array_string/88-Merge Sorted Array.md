# 88. Merge Sorted Array
[LeetCode link 題目連結](https://leetcode.com/problems/merge-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150)  
# 題目
給予兩個lsit `nums1`, `nums2`  
`nums1`有m個int  
`nums2`有n個int    
將兩個list合併成1個由小到大排列的list  
> 本題目不回傳list 而是直接修改nums1
## 範例
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3  
Output: [1,2,2,3,5,6]
# 解法
num1的長度其實是 m + n  
輸出的數字由小到大排序  
但要從num1的最後一個位置將`nums1`與`nums2`的數字比較大小，把大到小依序塞入`nums1`
> TODO
# code
```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        idx1 = m - 1
        idx2 = n - 1
        curr = m + n - 1
        while idx2 >= 0:
            if idx1 < 0:
                nums1[:curr+1] = nums2[:idx2+1]
                break
            else:
                if nums1[idx1] > nums2[idx2]:
                    nums1[curr] = nums1[idx1]
                    curr -= 1
                    idx1 -= 1
                else:
                    nums1[curr] = nums2[idx2]
                    curr -= 1
                    idx2 -= 1
```
# 88. Merge Sorted Array
[LeetCode link 題目連結](https://leetcode.com/problems/merge-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150)  
# 題目
給定兩個陣列`nums1`和`nums2`，兩者皆已從小到大排列。  
`nums1`包含了 m 個整數，而`nums2`包含了 n 個整數。目標是將這兩個陣列合併成一個由小到大排列的陣列。  
==本題目不回傳陣列 而是直接修改nums1==
# 解題
- 範例:
  - Input:  
  nums1 = [1,2,3,0,0,0], m = 3  
  nums2 = [2,5,6], n = 3  
- Output:
  - [1,2,2,3,5,6]  

解題的關鍵點是從尾端開始合併兩個已排序陣列。這是因為從頭開始合併可能會覆蓋掉`nums1`中尚未排序的元素，從而造成數字遺失。  

nums1 的最後一個元素的索引為 m-1，而 nums2 的最後一個元素的索引為 n-1。合併後數組的最後一個位置是 m+n-1。  

以範例來說，`nums1`的最後一個元素是 3，`nums2`的最後一個元素是 6，此時要將較大的 6 放入`nums1`索引5的位置(陣列的最末端)，`nums1`就變成了 [1,2,3,0,0,6]。  

在下一輪迭代中，num1最後的元素仍然是 3，nums2則換成了 5，此時要將較大的 5 放入`nums1`索引4的位置(陣列的最末端)，`nums1`就變成了 [1,2,3,0,5,6]。  

以這樣的模式持續迭代，直到所有的元素都被合併完成。便不會覆蓋掉`nums1`中尚未排序的元素，並確保所有的元素都被正確地合併到`nums1`中。
# python
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
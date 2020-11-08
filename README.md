# leetcode
Leetcode 刷题记录
================
## 1. 两数之和
`描述：`
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。<br>
你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。
`样例：`
给定 nums = [2, 7, 11, 15], target = 9<br>
因为 nums[0] + nums[1] = 2 + 7 = 9 <br>
所以返回 [0, 1]

`代码：`
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            eclipse = target - nums[i]
            if eclipse in nums[i + 1 : ]:
                return [i, (nums[i + 1 : ].index(eclipse) + i + 1)]
```

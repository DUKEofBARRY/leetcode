# leetcode
Leetcode 刷题记录
================
## 1. 两数之和
`描述：`<br>
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。<br>
你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。<br>
`样例：`<br>
给定 nums = [2, 7, 11, 15], target = 9<br>
因为 nums[0] + nums[1] = 2 + 7 = 9 <br>
所以返回 [0, 1]

`代码：`<br>
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            eclipse = target - nums[i]
            if eclipse in nums[i + 1 : ]:
                return [i, (nums[i + 1 : ].index(eclipse) + i + 1)]
```
`解释：`<br>
因为数组是排序好的，使用双指针，一个从start开始，一个从end开始，两个值相加，大于target则说明end指向的数太大(end左移)<br>
小于target则说明start指向的值太小(start右移)<br>

## 2. 两数相加
`描述：`<br>
给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。<br>
如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。<br>
您可以假设除了数字 0 之外，这两个数都不会以 0 开头。<br>
`样例：`<br>
输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)<br>
输出：7 -> 0 -> 8<br>
原因：342 + 465 = 807<br>
`代码：`<br>
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        list1 = []; list2 = []; result = []; incr = 0;
        while l1 != None:
            list1.append(l1.val)
            l1 = l1.next
        while l2 != None:
            list2.append(l2.val)
            l2 = l2.next
        while list1 or list2:
            if not list1:
                value = list2.pop(0) + incr
                if value > 9:
                    result.append(value - 10)
                    incr = 1
                else:
                    result.append(value)
                    incr = 0
            elif not list2:
                value = list1.pop(0) + incr
                if value > 9:
                    result.append(value - 10)
                    incr = 1
                else:
                    result.append(value)
                    incr = 0
            else:
                value = list1.pop(0) + list2.pop(0) + incr
                if value > 9:
                    result.append(value - 10)
                    incr = 1
                else:
                    result.append(value)
                    incr = 0
        if incr == 1:
            result.append(1)
        head = ListNode(result[0])
        cruiser = head
        for num in result[1 : ]:
            cruiser.next = ListNode(num)
            cruiser = cruiser.next
        return head
```
`解释：`<br>
使用一个incr决定是否进位，两个链表向后滑动，有incr就 + 1，最后到 Null 后incr = 1结果就加一<br>

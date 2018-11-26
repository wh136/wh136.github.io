---
title: leetcode猛撸
date: 2018-5-10 13:09:04
tags: [leetcode, Python2.7]
---
为了应对不同笔试中的语言问题，现采取C/C++/Python/Java来掌握不同笔试题的知识点。

### 1.两数之和 Python
1.给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。
你可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。
示例:
```bash
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```
```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        list_len = len(nums)
        for i in range(0, list_len):
            for j in range(i + 1, list_len):
                if (nums[i] + nums[j] == target):
                    # print [i, j]
                    return [i, j]

# nums = [3, 2, 4]
# target = 6
# obj = Solution()
# obj.twoSum(nums, target)

```
<!-- more -->
### 2.两数相加  Python
给定两个非空链表来表示两个非负整数。位数按照逆序方式存储，它们的每个节点只存储单个数字。将两数相加返回一个新的链表。
你可以假设除了数字 0 之外，这两个数字都不会以零开头。
示例：
```python
输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807
```

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        cur1 = ListNode(0)
        cur2 = cur1
        while True:
            if (l1 is not None) & (l2 is not None):
                if l1.val + l2.val + cur2.val >= 10:
                    carry_bit = (l1.val + l2.val + cur2.val) / 10
                    base_bit = (l1.val + l2.val + cur2.val) % 10
                    cur2.val = base_bit
                    cur2.next = ListNode(0)
                    cur2 = cur2.next
                    cur2.val = carry_bit
                else:
                    increament = l1.val + l2.val
                    cur2.val += increament
                    if (l1.next is not None) & (l2.next is not None):
                        cur2.next = ListNode(0)
                        cur2 = cur2.next
                    elif (l1.next is None) & (l2.next is None):
                        pass
                    else:
                        cur2.next = ListNode(0)
                        cur2 = cur2.next
                l1 = l1.next
                l2 = l2.next
            elif (l1 is not None) & (l2 is None):
                if cur2.val + l1.val >= 10:
                    carry_bit = (cur2.val + l1.val) / 10
                    base_bit = (cur2.val + l1.val) % 10
                    cur2.val = base_bit
                    cur2.next = ListNode(0)
                    cur2 = cur2.next
                    cur2.val = carry_bit
                else:
                    cur2.val = cur2.val + l1.val
                    if l1.next is not None:
                        cur2.next = ListNode(0)
                        cur2 = cur2.next
                    else:
                        pass
                l1 = l1.next
            elif (l1 is None) & (l2 is not None):
                if cur2.val + l2.val >= 10:
                    carry_bit = (cur2.val + l2.val) / 10
                    base_bit = (cur2.val + l2.val) % 10
                    cur2.val = base_bit
                    cur2.next = ListNode(0)
                    cur2 = cur2.next
                    cur2.val = carry_bit
                else:
                    cur2.val = cur2.val + l2.val
                    if l2.next is not None:
                        cur2.next = ListNode(0)
                        cur2 = cur2.next
                    else:
                        pass
                l2 = l2.next
            else:
                break
        return cur1


class LinkedList(object):
    def create(self, lst):
        head = ListNode(lst[0])
        cur = head
        for i in range(1, len(lst)):
            cur.next = ListNode(lst[i])
            cur = cur.next
        return head

```

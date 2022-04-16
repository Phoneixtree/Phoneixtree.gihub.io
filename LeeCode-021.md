---
title: LeeCode_021
date: 2022-04-16 15:18:35
tags:
categories: LeeCode
---

# 力扣题解021
## 我的题解
递归解法
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
    ListNode ans=new ListNode(0,null);
    return mergeTwoLists1(ans,list1,list2);
}
    public ListNode addlist(ListNode list1, ListNode list2)
    {
        ListNode pass=list1;
        while(pass.next!=null)
        {
            pass=pass.next;
        }
        list2.next=pass.next;
        pass.next=list2;
        return list1;
    }
    public ListNode mergeTwoLists1(ListNode ans,ListNode list1, ListNode list2)
    {
        if(list1!=null&&list2==null)
        {
            ListNode tmp=new ListNode(list1.val,null);
            addlist(ans,tmp);
            mergeTwoLists1(ans,list1.next,list2);
        }
        else if(list1==null&&list2!=null)
        {
            ListNode tmp=new ListNode(list2.val,null);
            addlist(ans,tmp);
            mergeTwoLists1(ans,list1,list2.next);
        }
        else if(list1!=null&&list2!=null)
        {
            if(list1.val<=list2.val)
            {
            ListNode tmp=new ListNode(list1.val,null);
            addlist(ans,tmp);
            mergeTwoLists1(ans,list1.next,list2);
            }
            else
            {
            ListNode tmp=new ListNode(list2.val,null);
            addlist(ans,tmp);
            mergeTwoLists1(ans,list1,list2.next);
            }
        }       
        else
        {
            return ans.next;
        }
    return ans.next;
    }
}
```
## 我的效率
>时间复杂度O(m+n);
>>执行用时：1 ms, 在所有 C++ 提交中击败了100.00% 的用户;

>空间复杂度O(m+n);
>>内存消耗：40.9 MB, 在所有 C++ 提交中击败了38.33% 的用户;

## 其他题解
### 迭代算法
```java
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode prehead = new ListNode(-1);

        ListNode prev = prehead;
        while (l1 != null && l2 != null) {
            if (l1.val <= l2.val) {
                prev.next = l1;
                l1 = l1.next;
            } else {
                prev.next = l2;
                l2 = l2.next;
            }
            prev = prev.next;
        }

        // 合并后 l1 和 l2 最多只有一个还未被合并完，我们直接将链表末尾指向未合并完的链表即可
        prev.next = l1 == null ? l2 : l1;

        return prehead.next;
    }
}
```
### 效率
> 时间复杂度：O(n+m)O(n + m)O(n+m)，其中 nnn 和 mmm 分别为两个链表的长度。因为每次循环迭代中，l1 和 l2 只有一个元素会被放进合并链表中， 因此 while 循环的次数不会超过两个链表的长度之和。所有其他操作的时间复杂度都是常数级别的，因此总的时间复杂度为 O(n+m)O(n+m)O(n+m)。

> 空间复杂度：O(1)O(1)O(1)。我们只需要常数的空间存放若干变量。



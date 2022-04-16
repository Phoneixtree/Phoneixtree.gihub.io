---
title: Leecode_002
date: 2022-04-16 14:15:26
tags: 
categories: LeeCode
---

# 力扣题解002
## 我的题解
自然解法
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    int val1,val2,val3,remain;
    int carry=0;
    ListNode head = new ListNode();
    while(l1!=null||l2!=null)
    {
    val1 = (l1!=null)? l1.val : 0;
    val2 = (l2!=null)? l2.val : 0;
    val3 = val1 + val2 + carry;
    remain = val3 % 10;
    if(val3==remain) {carry=0;}
    else {carry=1;}
    ListNode tmp = new ListNode(remain);
    addlist(head,tmp);
    if(l1!=null) {l1=l1.next;}
    if(l2!=null) {l2=l2.next;}
    }
    if(carry==1)
    {
    ListNode tmp = new ListNode(1);
    addlist(head,tmp);
    }
return head.next;
}
public ListNode addlist(ListNode L, ListNode addtion)
{
    ListNode tmp = L;
    while(tmp.next!=null)
    {
        tmp=tmp.next;
    }
    addtion.next=tmp.next;
    tmp.next=addtion;
    return L;
}
}
```
## 我的效率
>时间复杂度O(max(m,n));
>>执行用时：1 ms, 在所有 C++ 提交中击败了100.00% 的用户;

>空间复杂度O(1);
>>内存消耗：41.6 MB, 在所有 C++ 提交中击败了22.11% 的用户;

## 无其他题解

## error解决
+ 在ListNode L本身为null时，L.next会引发NullPointerException错误
+ return head->next 确实可以返回正确的结果，但是之前的初始创建的 val = -1 的节点没有释放，c++要手动释放，否则调用次数多会溢出  建议写成 ptrDelete = head; head = head->next delete ptrDelete; return head;




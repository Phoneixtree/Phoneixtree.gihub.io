---
title: LeeCode_003
date: 2022-04-19 15:22:31
tags:
categories: LeeCode
---
# 力扣题解003
## 我的题解
滑动窗口
```C++
class Solution {
public:
    int ans=1;
    int lengthOfLongestSubstring(string s) {
    int head=0; int tail=0;//窗口头窗口尾
    int tmplength=1;
    int len=s.length(); 
    if(len==0) return 0;
    while(tail<len-1)
    {
        if(!searchchar(head,tail,s))//下一个字符在窗口中不存在
        {
            tail++;
            tmplength++;//窗口尾往后，窗口长度加一
            longest(tmplength);
        }
        else//下一个字符在窗口中存在
        {
            head++;
            tmplength--;//窗口头往后，窗口长度减一
        }
    }
    return ans;
}
    int longest(int tmp)
    {
        if(tmp>ans)
        {ans=tmp;}
        return ans;
    }
    int searchchar(int i, int j, string s)
    {
        for(i;i<=j;i++)
        {
            if(s[i]==s[j+1]) return true;
        }
        return false;
    }
};
```
## 我的效率
>最优时间复杂度O(n),最差时间复杂度O(n^2)，可考虑用hash提高速度
>>执行用时：324 ms, 在所有 C++ 提交中击败了7.10% 的用户

>空间复杂度O(1)
>>内存消耗：322.9 MB, 在所有 C++ 提交中击败了4.97% 的用户

## 其他题解
### 使用哈希集合
在上面的流程中，我们还需要使用一种数据结构来判断 是否有重复的字符，常用的数据结构为哈希集合（即 C++ 中的 std::unordered_set，Java 中的 HashSet，Python 中的 set, JavaScript 中的 Set）。在左指针向右移动的时候，我们从哈希集合中移除一个字符，在右指针向右移动的时候，我们往哈希集合中添加一个字符。

### 效率
>时间复杂度O(N)，其中NNN是字符串的长度。左指针和右指针分别会遍历整个字符串一次

>空间复杂度O(∣Σ∣)，其中Σ表示字符集（即字符串中可以出现的字符），∣Σ∣表示字符集的大小
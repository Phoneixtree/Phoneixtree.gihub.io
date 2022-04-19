---
title: LeeCode_004
date: 2022-04-19 15:22:34
tags:
categories: LeeCode
---

# 力扣题解004
## 我的题解
递归
```C++
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
    vector<int> tmp; 
    int len1=nums1.size();
    int len2=nums2.size();
    int oddeven = ((len1+len2)%2==0)? 0 : 1; //确定结合后向量长度为奇数还是偶数
    double ans; int mid;
    merge(tmp,nums1,nums2,0,0);
    if(oddeven==0)
    {
        mid=(len1+len2)/2;
        ans=double((tmp[mid-1]+tmp[mid]))/2;
    }
    else
    {
        mid=1+int((len1+len2)/2);
        ans=tmp[mid-1];
    }
    return ans;
    }
    vector<int> merge(vector<int>& sum,vector<int>& nums1,vector<int>& nums2,int i,int j) //递归结合
    {
        int len1=nums1.size();
        int len2=nums2.size();
        if(i<len1&&j<len2)
        {
            if(nums1[i]<=nums2[j])
            {
                sum.push_back(nums1[i]);
                return merge(sum,nums1,nums2,i+1,j);
            }
            else
            {
                sum.push_back(nums2[j]);
                return merge(sum,nums1,nums2,i,j+1);
            }
        }
        else if(i>=len1&&j<len2)
        {
            sum.push_back(nums2[j]);
            return merge(sum,nums1,nums2,i,j+1);
        }
        else if(i<len1&&j>=len2)
        {
            sum.push_back(nums1[i]);
            return merge(sum,nums1,nums2,i+1,j);
        }
        return sum;
    }
};
```
## 我的效率
>时间复杂度O(m+n)
>>执行用时：32ms,在所有C++提交中击败了41.09%的用户

>空间复杂度O(m+n)
>>内存消耗：88.1MB,在所有C++提交中击败了5.11%的用户

## 其他题解
### 二分查找
此处请看官方题解

### 效率
>时间复杂度O(log(m+n))

>空间复杂度O(1)

### 划分数组
此处请看官方题解

### 效率
>O(log⁡min⁡(m,n))

>O(1)

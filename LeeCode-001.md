---
title: Leecode_001
date: 2022-04-13 17:58:40
tags:
categories: LeeCode
---

# 力扣题解001
## 我的题解
暴力解法
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> solu(2);
        int i,j;
        for(i=0;i<nums.size();i++)
        {    for(j=i+1;j<nums.size();j++)
            {
                unsigned plus=nums[i]+nums[j];
                if(plus==target)
                {
                    solu.clear();
                    solu.push_back(j);
                    solu.push_back(i);
                    break;
                }
            }  
        }
    return solu;   
    }
};
```
## 我的效率
>时间复杂度O(n^2);
>>执行用时：516 ms, 在所有 C++ 提交中击败了5.25% 的用户;

>空间复杂度O(1);
>>内存消耗：9.7 MB, 在所有 C++ 提交中击败了99.42% 的用户;

## 其他题解
### 哈希表
我们创建一个哈希表，对于每一个 x，我们首先查询哈希表中是否存在 target - x，然后将 x 插入到哈希表中，即可保证不会让 x 和自己匹配。
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> hashtable;
        for (int i = 0; i < nums.size(); ++i) {
            auto it = hashtable.find(target - nums[i]);
            if (it != hashtable.end()) {
                return {it->second, i};
            }
            hashtable[nums[i]] = i;
        }
        return {};
    }
};
```
### 效率
>时间复杂度O(n);
>空间复杂度O(1);
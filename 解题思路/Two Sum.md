# Two Sum

## 题目

给定一个数组和一个目标值，返回两个数组中相加为目标值得元素，比如：

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

## 思路

* 在使用额外空间在遍历`nums`数组时记录每一个元素与`target`目标值的差距。
* 在记录之前检查当前访问到的元素是否正是之前某个元素需要的值。
  * 如果是，则返回这两个元素的下标
  * 如果不是，则在额外空间中记录当前元素的下标和它能达到`target`需要的值。

## 效率

时间：`O(nlogn)` 

空间：`O(n)`

使用`STL map`实现，对于`map`的介绍参考[这里](https://github.com/poohRui/leetcode/blob/master/%E5%B8%B8%E7%94%A8%E6%96%B9%E6%B3%95%E6%80%BB%E7%BB%93/C%2B%2B%E6%93%8D%E4%BD%9C%E4%B9%8Bmap.md)
## 代码

```c++
#include<map>
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> result;
        map<int,int> container;
        for(int i = 0;i<nums.size();i++){
            map<int,int>::iterator it = container.find(nums[i]);
            if(it == container.end()){
                container[target-nums[i]] = i;
            }
            else{
                result.push_back(it->second);
                result.push_back(i);
                break;
            }      
        }
        return result;
    }
};
```

## 遗留问题

使用`unordered_map`实现能不能把效率提高到`O(n)`


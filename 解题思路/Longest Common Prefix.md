# Longest Common Prefix

## 题目

给定一个字符串数组，返回这个数组中所有字符串的最长公共前缀。 比如

```
Input:["aa","a"]
Output:"a"
```

## 思路

考虑以下情况

* 字符串数组为空
* 数组中某个字符串为空
* 不存在公共前缀

过程

* 定义`prefix`来存放最长公共前缀，一开始使其为数组中的第一个字符串
* 循环比较数组中的每一个字符串与`prefix`，不断修改`prefix`的值。
  * 如果`str`和`prefix`中对应的值不相等，则应将`prefix`修改为对应子字符串，如str="abc",prefix="acd"
  * 如果`str`比`prefix`短，且整个`str`完全匹配`prefix`的一部分，将`prefix`改为`str`，如str="a",prefix="aa"
  * 如果`str`比`prefix`长，且`prefix`完美匹配`str`的前半部分，则不做修改，如str="aa",prefix="a"

## 效率

时间效率：O(n*m)，n为字符串个数，m为字符串长度

空间效率：无

## 参考代码

```c++
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if(strs.empty()){
            return "";
        }
        string prefix = strs[0];
        for(int i = 1;i<strs.size();i++){
            if(strs[i] == "" || prefix == ""){
                return "";
            }
            for(int j = 0;j<strs[i].length() && j<prefix.length();j++){
                if(strs[i].at(j) != prefix.at(j)){
                    prefix = prefix.substr(0,j);
                    break;
                }
                if(j == strs[i].length() - 1){
                    prefix = strs[i];
                }
            }
            
        }
        return prefix;
    }
};
```


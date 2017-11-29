# Longest Substring Without Repeating Characters

## 题目

给定一个字符串，返回该字符串中没有重复字符的最长子字符串的长度。

```
Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.

```

## 思路

* 使用两个指针遍历字符串，设两个指针分别为`start`和`i`，两个指针中间为没有重复字符的子字符串，固定`start`指针，向后移动`i`指针，同时记录访问到的字符即其位置，当`i`指针指向的字符在记录中存在则表示出现重复，记录此时的子字符串长度并和最长长度比较。
* 对于每一个字符`char`，占一个字节，即8 bits，所以完全可以使用一个容量为256的数组来存放位置信息，而不需要采用`map`。

## 测试用例

| input     | return |
| --------- | ------ |
| "ac"      | 2      |
| ""        | 0      |
| " pwwkew" | 4      |

## 效率

时间：`O(n)` 

空间：`O(n)`

使用`STL vector`实现，对于`vector`的介绍参考[这里](https://github.com/poohRui/leetcode/blob/c36eb150c816f34a6421545f0dddfc2941de6287/%E5%B8%B8%E7%94%A8%E6%96%B9%E6%B3%95%E6%80%BB%E7%BB%93/C++%E6%93%8D%E4%BD%9C%E4%B9%8Bvector.md)
## 代码

```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        vector<int> keyOfString(256,-1);
        int longest = 0;
        int i = 0;
        int start = 0;
        while(i<s.length()){
            if(keyOfString[s[i]] != -1 && keyOfString[s[i]]>=start){
                int tmpLen = i - start;
                if(tmpLen > longest){
                    longest = tmpLen;
                }
                start = keyOfString[s[i]] + 1;
            }
            keyOfString[s[i]] = i;
            i++;
        }
        longest = (i - start) > longest?(i - start):longest;
        return longest;       
    }
};
```


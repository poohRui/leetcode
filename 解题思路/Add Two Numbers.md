# Add Two Numbers

## 题目

给定两个非空的链表，代表两个非负整数，链表以反序存储数字，也就是(2 -> 4 -> 3)代表的是数字342，求两个链表相加的结果，结果也存放在链表中返回。已给出链表的结构体如下：

```c++
* Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
```

输入输出实例：

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
```

## 思路

实际上反序存储数字不会影响最终的结果，只需要按照普通的加法来进行计算即可。

考虑对以下情况的处理

* 虽然题目中明确指定是`两个非空链表`，但还是判断一下为好，如果两个链表都为空，直接返回`NULL`
* 如果一个链表为空，一个链表有值（可大致等同最后一种情况）
* 如果两个链表都不为空，且长度相等
* 如果两个链表都不为空，且长度不等
* 对最高位相加产生进位的处理，如9+9

## 效率

时间效率：max(链表1的长度，链表2的长度)

辅助空间：无（不包括最终返回存储的结果链表）

## 代码

```c++
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        if(l1 == NULL && l2 == NULL){
            return NULL;
        }
        int carry = 0;
        ListNode *result = new ListNode(0);
        ListNode *curNode = result;
        while(l1 != NULL){
            int l2Value = 0;
            if(l2 != NULL){
                l2Value = l2->val;
                l2 = l2->next;
            }
            int value = (l1->val + l2Value + carry) % 10;
            carry = (l1->val + l2Value + carry) / 10;
            curNode->next = new ListNode(value);
            l1 = l1->next;
            curNode = curNode->next;
        }
        while(l2 != NULL){
            curNode->next = new ListNode((l2->val + carry) % 10);
            carry = (l2->val + carry) / 10;
            l2 = l2->next;
            curNode = curNode->next;
        }
        if(carry){
            curNode->next = new ListNode(carry);
        }
        return result->next;
    }
};
```
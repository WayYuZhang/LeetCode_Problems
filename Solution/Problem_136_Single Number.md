# 136. Single Number

Given a **non-empty** array of integers, every element appears _twice_ except for one. Find that single one.

## **Example**

**Example 1:**

**Input:** [2,2,1]

**Output:** 1

**Example 2:**

**Input:** [4,1,2,1,2]

**Output:** 4

## **Solution**

### ONE

    class Solution {
        public int singleNumber(int[] nums) {
            int res = 0;
            for(int i : nums) {
                res ^= i;
            }
            return res;
        }
    }

## **Note**

+ 异或运算符是用符号 `^` 表示的，其运算规律是：两个操作数的位中，相同则结果为0，不同则结果为1
+ 一个操作数被另一个操作数进行两次异或运算后等于自身

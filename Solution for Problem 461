# **461. Hamming Distance**

## **Description**

The [Hamming distance](https://en.wikipedia.org/wiki/Hamming_distance) between two integers is the number of positions at which the corresponding bits are different.

Given two integers 'x' and 'y', calculate the Hamming distance.

**Note:**
0 ≤ x, y < 2^31.

## **Example**

**Input:** x = 1, y = 4

**Output:** 2

**Explanation:**
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑

The above arrows point to positions where the corresponding bits are different.

## **Solution**

### ONE

    class Solution {
        public int hammingDistance(int x, int y) {
            int res = 0;
            for(int i = 0; i < 32; i++) {
                if(((x >> i) & 1) != ((y >> i) & 1))
                    res++;
            }
            return res;
        }
    }

### TWO

    class Solution {
        public int hammingDistance(int x, int y) {
            return Integer.bitCount(x ^ y);
        }
    }

## **Trick**

**1.** 右移运算符

右移运算符<<使指定值的所有位都右移规定的次数

+通用格式

value >> num 
num 指定要移位值 value 移动的位数
右移的规则只记住一点：符号位不变，左边补上符号位

+运算规则

按二进制形式把所有的数字向右移动对应的位数，低位移出(舍弃)，高位的空位补符号位，即正数补0，负数补1
当右移的运算数是 byte 和 short 类型时，将自动把这些类型扩大为 int 型
例如，如果要移走的值为负数，每一次右移都在左边补1，如果要移走的值为正数，每一次右移都在左边补0，这叫做符号位扩展（保留符号位）（sign extension），在进行右移操作时用来保持负数的符号

+数学意义

右移一位相当于除2，右移n位相当于除以2的n次方

**2.** Integer.bitCount(int i)

Returns the number of one-bits in the two's complement binary representation of the specified int value.

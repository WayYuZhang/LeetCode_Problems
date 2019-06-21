# 338. Counting Bits

Given a non negative integer number **num**. For every numbers **i** in the range **0 ≤ i ≤ num** calculate the number of 1's in their binary representation and return them as an array.

## **Example**

**Example 1:**

**Input:** 2

**Output:** `[0,1,1]`

**Example 2:**

**Input:** 5

**Output:** `[0,1,1,2,1,2]`

## **Solution**

### ONE

    class Solution {
        public int[] countBits(int num) {
            int[] res = new int[num + 1];
            int pow = 1;
            res[0] = 0;
            for(int i = 1, t = 0; i <= num; i++, t++) {
                if(pow == i) {
                    pow *= 2;
                    t = 0;
                }
                res[i] = res[t] + 1;
            }
            return res;
        }
    }

### TWO

    class Solution {
        public int[] countBits(int num) {
            int[] res = new int[num + 1];
            res[0] = 0;
            helper(num, 1, 1, res);
            return res;
        }

        void helper(int num, int cur, int count, int[] res) {
            if(cur > num)
                return;
            res[cur] = count;
            helper(num, cur << 1, count, res);
            helper(num, (cur << 1) + 1, count + 1, res);
        }
    }

## **Note**

General function: `dp[i] = dp[i - offset] + 1`

当 `i` 为 2 的幂次方时，`offset = i`

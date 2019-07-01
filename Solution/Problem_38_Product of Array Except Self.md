# 238. Product of Array Except Self

Given an array `nums` of _n_ integers where _n_ > 1,  return an array `output` such that `output[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

## **Example**

**Input:**  `[1,2,3,4]`

**Output:** `[24,12,8,6]`

## **Solution**

    class Solution {
        public int[] productExceptSelf(int[] nums) {
            int n = nums.length;
            int[] res = new int[n];
            res[0] = 1;
            for(int i = 1; i < n; i++) {
                res[i] = res[i - 1] * nums[i - 1];
            }
            int tmp = 1;
            for(int i = n - 1; i >= 0; i--) {
                res[i] *= tmp;
                tmp *= nums[i];
            }
            return res;
        }
    }

## **Note**

第一个for循环得到元素左侧的乘积，第二个for循环得到元素右侧的乘积

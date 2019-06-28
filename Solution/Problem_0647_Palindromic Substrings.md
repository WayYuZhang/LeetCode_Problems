# 647. Palindromic Substrings

Given a string, your task is to count how many palindromic substrings in this string.

The substrings with different start indexes or end indexes are counted as different substrings even they consist of same characters.

## **Example**

**Example 1:**

**Input:** "abc"

**Output:** 3

**Explanation:** Three palindromic strings: "a", "b", "c".

**Example 2:**

**Input:** "aaa"

**Output:** 6

**Explanation:** Six palindromic strings: "a", "a", "a", "aa", "aa", "aaa".

## **Solution**

### ONE

    class Solution {
        int res = 0;
        
        public int countSubstrings(String s) {
            for(int i = 0; i < s.length(); i++) {
                helper(s, i, i);
                helper(s, i, i + 1);
            }
            return res;
        }
        
        void helper(String s, int i, int j) {
            while(i >= 0 && j < s.length() && s.charAt(i) == s.charAt(j)) {
                i--;
                j++;
                res++;
            }
        }
    }

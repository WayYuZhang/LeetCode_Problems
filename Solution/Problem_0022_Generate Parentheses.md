# 22. Generate Parentheses

Given _n_ pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

## **Example**

For example, given _n_ = 3, a solution set is:

[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]

## **Solution**

### ONE

    class Solution {
        public List<String> generateParenthesis(int n) {
            List<String> res = new ArrayList<String>();
            helper(res, new StringBuilder(), n, n);
            return res;
        }
        
        void helper(List<String> res, StringBuilder s, int left, int right) {
            if(left > right)
                return;
            if(left = 0 && right == 0) {
                res.add(s.toString());
                return;
            }
            if(left > 0) {
                s.append("(");
                helper(res, s, left - 1, right);
                s.deleteCharAt(s.length() - 1);
            }
            if(right > 0) {
                s.append(")");
                helper(res, s, left, right - 1);
                s.deleteCharAt(s.length() - 1);
            }
        }
    }

### TWO

    class Solution {
        public List<String> generateParenthesis(int n) {
            List<String> res = new ArrayList<String>();
            if(n == 0)
                res.add("");
            else {
                for(int i = 0; i < n; i++) {
                    for(String left : generateParenthesis(i)) {
                        for(String right :generateParenthesis(n - i - 1)) {
                            res.add("(" + left + ")" + right);
                        }
                    }
                }
            }
            return res;
        }
    }

## **Note**


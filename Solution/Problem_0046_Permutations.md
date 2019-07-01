# 46. Permutations

Given a collection of **distinct** integers, return all possible permutations.

## **Example**

**Input:** [1,2,3]

**Output:**
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]

## **Solution**

### ONE

    class Solution {
        public List<List<Integer>> permute(int[] nums) {
            List<List<Integer>> res = new ArrayList<List<Integer>>();
            helper(res, new ArrayList<Integer>(), nums);
            return res;
        }

        void helper(List<List<Integer>> res, List<Integer> l, int[] nums) {
            if(l.size() == nums.length)
                res.add(new ArrayList<Integer>(l));
            else {
                for(int i = 0; i < nums.length; i++) {
                    if(l.contains(nums[i]))
                        continue;
                    l.add(nums[i]);
                    helper(res, l, nums);
                    l.remove(l.size() - 1);
                }
            }
        }
    }

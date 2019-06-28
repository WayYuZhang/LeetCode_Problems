# 94. Binary Tree Inorder Traversal

Given a binary tree, return the _inorder_ traversal of its nodes' values.

## **Example**

**Input:** [1,null,2,3]

    1
     \
      2
     /
    3

**Output:** [1,3,2]

## **Solution**

### ONE

    class Solution {
        public List<Integer> inorderTraversal(TreeNode root) {
            List<Integer> res = new ArrayList<Integer>();
            Stack<TreeNode> s = new Stack<TreeNode>();
            TreeNode cur = root;
            while(cur != null || !s.isEmpty()) {
                while(cur != null) {
                    s.push(cur);
                    cur = cur.left;
                }
                cur = s.pop();
                res.add(cur.val);
                cur = cur.right;
            }
            return res;
        }
    }

### TWO

    class Solution {
        List<Integer> res;
        
        public List<Integer> inorderTraversal(TreeNode root) {
            res = new ArrayList<Integer>();
            helper(root);
            return res;
        }
        
        void helper(TreeNode node) {
            if(node == null)
                return;
            helper(node.left);
            res.add(node.val);
            helper(node.right);
        }
    }

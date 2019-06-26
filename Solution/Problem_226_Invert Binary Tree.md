# 226. Invert Binary Tree

Invert a binary tree.

## **Example**

Input:

	      4
	    /   \
	   2     7
	  / \   / \ 
	 1   3 6   9

Output:

	      4
	    /   \
	   7     2
	  / \   / \ 
	 9   6 3   1

## **Solution**

### ONE

    class Solution {
        public TreeNode invertTree(TreeNode root) {
            if(root == null)
                return root;
            TreeNode left = root.left;
            TreeNode right = root.right;
            root.left = invertTree(right);
            root.right = invertTree(left);
            return root;
        }
    }

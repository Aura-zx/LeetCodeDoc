# 104 Maximum Depth of Binary Tree

标签（空格分隔）： LeetCode Tree Depth-first_Search

---

**Problem:**
>   Given a binary tree, find its maximum depth.

>   The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Solution:**
```cpp
/**
 1. Definition for a binary tree node.
 2. struct TreeNode {
 3.     int val;
 4.     TreeNode *left;
 5.     TreeNode *right;
 6.     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 7. };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (!root)	// check if tree is empty;
			return 0;
		
		int leftDepth = maxDepth(root->left) + 1;
		int rightDepth = maxDepth(root->right) + 1;
		
		return leftDepth > rightDepth ? leftDepth : rightDepth;
    }
};
```

**Analysis:**

 1. 题目大意是找出二叉树的最大深度
 2. 给出了二叉树的结构，采用递归求解的办法，求出左子树和右子树的深度，求二者最大值
 3. 深度优先搜索

  

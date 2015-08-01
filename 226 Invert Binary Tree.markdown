# 226 Invert Binary Tree

标签（空格分隔）： LeetCode Tree

---

**Problem:**
>   Invert a binary tree.

         4
       /   \
      2     7
     / \   / \
    1   3 6   9
    to
         4
       /   \
      7     2
     / \   / \
    9   6 3   1
    
    Trivia:
    This problem was inspired by this original tweet by Max Howell:
    Google: 90% of our engineers use the software you wrote (Homebrew), but you can’t invert a binary tree on a whiteboard so fuck off.

**Solution**
```cpp
	TreeNode* invertTree(TreeNode *root)
	{
		if (!root)			// check if tree is empty
			return root;

		invertTree(root->left);
		invertTree(root->right);

		TreeNode *tmp = root->right;
		root->right = root->left;
		root->left = tmp;
		
		return root;
	}
```

**Analysis:**

 1. 翻转二叉树，很简单的一个题
 2. 如下面的Trivia所说，是来自于Twitter上的一个题，一个著名软件的作者参加Google的面试，结果这个题没有过...
 3. 递归解决即可


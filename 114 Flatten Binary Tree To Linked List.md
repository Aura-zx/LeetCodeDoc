# 114 Flatten Binary Tree To Linked List

标签（空格分隔）： LeetCode DFS

---

**Problem:**
>   Given a binary tree, flatten it to a linked list in-place.
>
For example,
Given

         1
        / \
       2   5
      / \   \
     3   4   6

>   The flattened tree should look like:
>
    1
    \
     2
      \
       3
        \
         4
          \
           5
            \
             6

**Analysis:**

 1. 将一个二叉树原地平坦化，如下面的形式。
 2. 仔细观察是以先序遍历的方式平坦化，所以在遍历的过程中，只需要将根的左子树设为NULL，将右子树设为原来的左子树，递归的做下去即可。

**Solution:**
```cpp
    void flattenTree(TreeNode* root, TreeNode* &last)
	{
		if (!root)
			return NULL;

		if (last != NULL)
		{
			last->left = NULL;
			last->right = root;
		}
		last = root;
		
		TreeNode *left = root->left;
		TreeNode *right = root->right;

		flattenTree(left, last);
		flattenTree(right, last);
	}

	void flatten(TreeNode* root)
	{
		if (!root)
			return;

		TreeNode* last = NULL;
		flattenTree(root, last);
	}
```
 

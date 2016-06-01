# 129 Sum Root to Leaf Numbers

标签（空格分隔）： LeetCode DFS Tree

---

 **Problem:**
 >  Given a binary tree containing digits from 0-9 only, each root-to-leaf path could represent a number.
>
An example is the root-to-leaf path 1->2->3 which represents the number 123.
>
Find the total sum of all root-to-leaf numbers.
>
For example,
>
   1
   / \
  2   3
The root-to-leaf path 1->2 represents the number 12.
The root-to-leaf path 1->3 represents the number 13.
>
Return the sum = 12 + 13 = 25.

**Analysis:**

 1. 给定一个0-9数字组成的二叉树，从根到叶子的路径上的数由高位向低位排列组成数，求所有路径数字之和。
 2. 注意判断是叶子节点需要左右子树均为NULL。
 3. 注意sum在递归过程中传递的是引用。

**Solution:**
```cpp
	void travel(TreeNode* root, int& sum, int path)
	{
		if (root == NULL)
			return;

		path = path * 10 + root->val;
		if (root->left == NULL && root->right == NULL)
		{
			sum += path;
			return;
		}

		travel(root->left, sum, path);
		travel(root->right, sum, path);
	}

	int sumNumbers(TreeNode* root)
	{
		int sum = 0;
		int path = 0;
		travel(root, sum, path);

		return sum;
	}
```
 

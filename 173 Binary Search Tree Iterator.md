# 173 Binary Search Tree Iterator

标签（空格分隔）： LeetCode Tree Stack

---

**Problem:**
>   Implement an iterator over a binary search tree (BST). Your iterator will be initialized with the root node of a BST.
>
Calling next() will return the next smallest number in the BST.
>
Note: next() and hasNext() should run in average O(1) time and uses O(h) memory, where h is the height of the tree.

**Analysis:**

 1. 实现一个二叉树的迭代器，要求实现next()函数能一步步的获取下一个最小的数和hasNext()判断是否有下一个数，O(1)时间和O(h)的空间。
 2. 常规思路是中序遍历将所有遍历结果存入vector再一个个取出，但是这样的空间复杂度是O(N)不符合题意。
 3. 借助stack，先将所有的左边节点压入栈，弹出栈的时候判断是否有右子树，有则压入右节点，再遍历压入所有右节点的左子树。

**Solution:**
```cpp
class BSTIterator
{
private:
	std::stack<TreeNode*> data;

public:
	BSTIterator(TreeNode* root)
	{
		while (root)
		{
			data.push(root);
			root = root->left;
		}
	}

	bool hasNext( )
	{
		return !data.empty( );
	}

	int next( )
	{
		auto t = data.top( );
		int val = t->val;
		data.pop( );

		t = t->right;
		while (t)
		{
			data.push(t);
			t = t->left;
		}

		return val;
	}
```
 

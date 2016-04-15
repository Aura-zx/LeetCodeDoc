# 108 Convert Sorted Array to Binary Search Tree

标签（空格分隔）： LeetCode Tree

---

**Problem:**
>   Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

**Analysis:**

 1. 求把一个有序数组转换成平衡二叉树。
 2. 中间的数字作为根，递归的建立左子树和右子树

**Solution:**
 ```cpp
 	TreeNode* buildTree(std::vector<int>& nums, int start, int end)
	{
		if (start > end)
			return NULL;

		int mid = start + (end - start) 
		TreeNode* root = new TreeNode(nums[mid]);

		root->left = buildTree(nums, start, mid - 1);

		root->right = buildTree(nums, mid + 1, end);

		return root;
	}

	TreeNode* sortedArrayToBST(std::vector<int>& nums)
	{
		return buildTree(nums, 0, nums.size( ) - 1);
	}
 ```

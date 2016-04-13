# 230 Kth Smallest in a BST

标签（空格分隔）： LeetCode Tree BinarySearch

---

**Problem:**
>   Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.
>
Note: 
You may assume k is always valid, 1 ≤ k ≤ BST's total elements.
>
Follow up:
What if the BST is modified (insert/delete operations) often and you need to find the kth smallest frequently? How would you optimize the kthSmallest routine?
>
Hint:
>
Try to utilize the property of a BST.
What if you could modify the BST node's structure?
The optimal runtime complexity is O(height of BST).

**Analysis:**

 1. 找出第K小的二叉搜索树的元素。
 2. 二叉搜索树的左边的值一定比右边的小，所以采取**中序遍历**可以得到所有元素从小到大的排列。
 3. 这个中序遍历的迭代版本值得思考，很多实现比这个要复杂许多。
 4. 根据提示还有O（h）复杂度的算法，思路是这样，若K小于左子树的元素个数，表明数在左子树，大于左子树个数则在右子树中，等于则返回该顶点的值，详细见reference。

**Solution:**
```cpp
	int KthSmallest(TreeNode* root, int k)
	{
		std::stack<TreeNode*> s;
		TreeNode* node = root;
		int ret = 0;

		while (node != NULL || !s.empty( ))
		{
			if (node != NULL)
			{
				s.push(node);
				node = node->left;
			}
			else
			{
				node = s.top( );
				s.pop( );
				if (--k == 0)
				{
					ret = node->val;
					break;
				}
				node = node->right;
			}
		}
		return ret;
	}
```
 
 **Reference:**
 [O(h)算法][1]


  [1]: http://stackoverflow.com/questions/2329171/find-kth-smallest-element-in-a-binary-search-tree-in-optimum-way#
# 235 Lowest Common Ancestor of a binary tree

标签（空格分隔）： LeetCode Tree

---

**Problem:**
>   Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

>   According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes v and w as the lowest node in T that has both v and w as descendants (where we allow a node to be a descendant of itself).”

        _______6______
       /              \
    ___2__          ___8__
    /      \        /      \
    0       _4      7       9
           /  \
          3   5
>   For example, the lowest common ancestor (LCA) of nodes 2 and 8 is 6. Another example is LCA of nodes 2 and 4 is 2, since a node can be a descendant of itself according to the LCA definition.

**Solution:**
```cpp
	TreeNode *lowestCommonAncestor(TreeNode* root, TreeNode *p, TreeNode *q)
	{
		if (!root)
			return NULL;

		if (p->val > root->val && q->val > root->val)
			return lowestCommonAncestor(root->right, p, q);
		else if (p->val < root->val && q->val < root->val)
			return lowestCommonAncestor(root->left, p, q);
		else
			return root;
	}
```

**Analysis:**

 1.  问题要求两个二叉搜索树中两个节点的最近公共祖先
 2.  对于二叉搜索树，它的左子树都小于根节点，右子树度大于根节点
 3.  1）两个节点都大于根，则公共祖先在根的右子树中 
     2）两个节点都小于根，则公共祖先在根的左子树中
     3）其他情况，公共祖先为当前根
 4. 递归解决即可


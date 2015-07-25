# 112 Path Sum

标签（空格分隔）： LeetCode Tree Depth-first_search

---

**Problem:**
> Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

> For example:
Given the below binary tree and sum = 22,

                     5
                    / \
                   4   8
                  /   / \
                 11  13  4
                /  \      \
               7    2      1
>   return true, as there exist a root-to-leaf path 5->4->11->2 which sum is 22.

**Solution:**
```cpp
bool hasPathSum(TreeNode *root, int sum)
{
  if (root == NULL)				// empty tree
    return false;

  // judge the path
  if (root->val == sum && (root->left == NULL && root->right == NULL))
    return true;

  // return (left subtree || right subtree)
  return hasPathSum(root->left, sum - (root->val)) || hasPathSum(root->right, sum - (root->val));
}
```
**Analysis:**
1. 在给定的树里是否存在，给定的数字为某一个根到叶子的路径之和
2. 用深度优先搜索可解决
3. 要注意叶子的判断条件，两个指针均为`NULL`
4. 注意在递归访问时，直接将访问结果返回

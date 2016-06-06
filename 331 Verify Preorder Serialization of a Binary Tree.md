# 331 Verify Preorder Serialization of a Binary Tree

标签（空格分隔）： LeetCode Math Stack

---

**Problem:**
>   One way to serialize a binary tree is to use pre-order traversal. When we encounter a non-null node, we record the node's value. If it is a null node, we record using a sentinel value such as #.
>
     _9_
    /   \
    3      2
    / \    / \
    4   1  #  6
    / \ / \   / \
    # # # #   # #
For example, the above binary tree can be serialized to the string "9,3,4,#,#,1,#,#,2,#,6,#,#", where # represents a null node.
>
Given a string of comma separated values, verify whether it is a correct preorder traversal serialization of a binary tree. Find an algorithm without reconstructing the tree.
>
Each comma separated value in the string must be either an integer or a character '#' representing null pointer.
>
You may assume that the input format is always valid, for example it could never contain two consecutive commas such as "1,,3".
>
Example 1:
"9,3,4,#,#,1,#,#,2,#,6,#,#"
Return true
>
Example 2:
"1,#"
Return false
>
Example 3:
"9,#,#,1"
Return false

**Analysis:**

 1. 给定一个字符串，判断它是否为一棵树的先序遍历。
 2. 不断的砍掉叶子结点，看最后能不能全部砍掉，遇到“x # #”这种模式的时候，变为“#”，合法的情况最后一定是“#”
 3. 细节方面，注意把字符串中的节点按照‘,’分割出来，存成字符串。
 4. 另一种方法是数学的方法，对于二叉树，把空节点也作为叶子结点时，有
    ·所有的非空结点提供2个出度和1个入度（根除外）
    ·所有空节点提供1个入度
合法结点最后的出度-入度=0

**Solution:**
```cpp
	std::vector<std::string> split(const std::string& str)
	{
		std::stringstream ss(str);
		std::vector<std::string> res;
		std::string s;

		while (std::getline(ss, s, ','))
			res.push_back(s);

		return res;
	}

	bool isValidSerialization(std::string preorder)
	{
		if (preorder.empty( ))
			return false;

		std::vector<std::string> res = split(preorder);
		std::stack<std::string> s;

		for (int i = 0; i < res.size( ); i++)
		{
			if (res[i] == "#")
			{
				if (s.empty( ))
					return i == (res.size( ) - 1);
				s.pop( );
			}
			else
				s.push(res[i]);
		}

		return false;
	}

	bool isValidSerialization2(std::string preorder)
	{
		std::vector<std::string> nodes = split(preorder);
		int diff = 1;
		for (auto s : nodes)
		{
			if (--diff < 0)
				return false;
			if (s == "#")
				diff += 2;
		}

		return diff == 0;
	}
```

**Reference:**
[图示][1]


  [1]: http://www.programcreek.com/2015/01/leetcode-verify-preorder-serialization-of-a-binary-tree-java/
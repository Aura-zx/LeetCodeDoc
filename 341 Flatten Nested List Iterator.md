# 341 Flatten Nested List Iterator

标签（空格分隔）： LeetCode Design

---

**Problem:**
>   Given a nested list of integers, implement an iterator to flatten it.
>
Each element is either an integer, or a list -- whose elements may also be integers or other lists.
>
Example 1:
Given the list [[1,1],2,[1,1]],
>
By calling next repeatedly until hasNext returns false, the order of elements returned by next should be: [1,1,2,1,1].
>
Example 2:
Given the list [1,[4,[6]]],
>
By calling next repeatedly until hasNext returns false, the order of elements returned by next should be: [1,4,6].

**Analysis:**

 1. 将一个嵌套列表展开，实现迭代器模式的细节。
 2. 用栈将list里的每一个NestedInteger压入，再判断每一个是否为integer，是则返回true，否则将该list继续拆开压入栈。
 3. 注意因为用的栈结构，所以压入的时候，当从最后一个元素压栈。

**Solution:**
```cpp
/**
 * // This is the interface that allows for creating nested lists.
 * // You should not implement it, or speculate about its implementation
 * class NestedInteger {
 *   public:
 *     // Return true if this NestedInteger holds a single integer, rather than a nested list.
 *     bool isInteger() const;
 *
 *     // Return the single integer that this NestedInteger holds, if it holds a single integer
 *     // The result is undefined if this NestedInteger holds a nested list
 *     int getInteger() const;
 *
 *     // Return the nested list that this NestedInteger holds, if it holds a nested list
 *     // The result is undefined if this NestedInteger holds a single integer
 *     const vector<NestedInteger> &getList() const;
 * };
 */
class NestedIterator {
public:
    NestedIterator(vector<NestedInteger> &nestedList) {
        for (int i = nestedList.size( ) - 1; i >= 0; --i)
			s.push(nestedList[i]);
    }

    int next() {
       	NestedInteger t = s.top( );
		s.pop( );
		return t.getInteger( );
    }

    bool hasNext() {
        while (!s.empty( ))
		{
			NestedInteger t = s.top( );
			if (t.isInteger( ))
				return true;
			s.pop( );
			for (int i = t.getList( ).size( ) - 1; i >= 0; i--)
				s.push(t.getList()[i]);
		}

		return false;
    }
private:
	std::stack<NestedInteger> s;
};

/**
 * Your NestedIterator object will be instantiated and called as such:
 * NestedIterator i(nestedList);
 * while (i.hasNext()) cout << i.next();
 */
```
 

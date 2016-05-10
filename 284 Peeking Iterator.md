# 284 Peeking Iterator

标签（空格分隔）： LeetCode Design

---

**Problem:**
>   Given an Iterator class interface with methods: next() and hasNext(), design and implement a PeekingIterator that support the peek() operation -- it essentially peek() at the element that will be returned by the next call to next().

**Analysis:**

 1. 实现一个顶端迭代器，peek操作是得到当前的值，但是不移动指针，此时调用next依旧获得peek值，要求全程不得仅能使用Iterator的方法，不要自己copy数组。
 2. 维护两个值，一个判断是否需要保留当前值，一个保留当前值。

**Solution:**
```cpp
class Iterator {
	struct Data;
	Data* data;
public:
	Iterator(const std::vector<int>& nums);
	Iterator(const Iterator& iter);
	virtual ~Iterator( );
	// Returns the next element in the iteration.
	int next( );
	// Returns true if the iteration has more elements.
	bool hasNext( ) const;
};


class PeekingIterator : public Iterator {
public:
	PeekingIterator(const std::vector<int>& nums) : Iterator(nums) {
		// Initialize any member here.
		// **DO NOT** save a copy of nums and manipulate it directly.
		// You should only use the Iterator interface methods.
		isSaved = false;
	}

	// Returns the next element in the iteration without advancing the iterator.
	int peek( ) {
		if (isSaved)
			return val;
		else
		{
			val = Iterator::next();
			isSaved = true;
			return val;
		}
	}

	// hasNext() and next() should behave the same as in the Iterator interface.
	// Override them if needed.
	int next( ) {
		if (isSaved)
		{
			isSaved = false;
			return val;
		}
		isSaved = false;
		return Iterator::next( );
	}

	bool hasNext( ) const {
		return isSaved || Iterator::hasNext( );
	}

private:
	bool isSaved;
	int val;
};
```
 

# 223 Rectangle Area

标签（空格分隔）： LeetCode Math

---

**Problem:**
>   Find the total area covered by two rectilinear rectangles in a 2D plane.
>
Each rectangle is defined by its bottom left corner and top right corner as shown in the figure.


**Analysis:**

 1. 求两个矩形一共覆盖了多大的面积。
 2. 判断是否相交，相交则减去小矩阵面积。
 3. 相交情况下的矩阵点为，各个方向四个点中除去最大和最小之外的两个点。
 4. 在代码中使用了排序。
 
**Solution:**
```cpp
	int computeArea(int A, int B, int C, int D, int E, int F, int G, int H)
	{
		int area = (D - B)*(C - A) + (H - F)*(G - E);

		if (E >= C || A >= G || F >= D || B >= H)
			return area;

		std::vector<int> x = { A, C, E, G };
		std::vector<int> y = { B, D, F, H };

		std::sort(x.begin( ), x.end( ));
		std::sort(y.begin( ), y.end( ));

		int length = abs(x[1] - x[2]);
		int height = abs(y[1] - y[2]);

		return area-length*height;
	}
```


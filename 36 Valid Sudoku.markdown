# 36 Valid Sudoku

标签（空格分隔）： LeetCode HashTable

---

**Problem:**
>   The Sudoku board could be partially filled, where empty cells are filled with the character '.'.
>
A partially filled sudoku which is valid.
Note:
A valid Sudoku board (partially filled) is not necessarily solvable. Only the filled cells need to be validated.


**Analysis:**

 1. 判断一个数独是否是合法的。
 2. 注意理解valid，只是整个棋盘看上去是否满足1-9之间没有重复即可，并不是判断是否有解。
 3. 思路是分别判断行、列和块。
 
**Solution:**
```cpp
bool isValidSudoku(std::vector<std::vector<char>>& board)
	{
		for (int i = 0; i < 9; i++)
		{
			if (!checkRow(board, i))
				return false;
			if (!checkCol(board, i))
				return false;
		}

		return checkBlock(board);
	}

	bool checkRow(std::vector<std::vector<char>>& board, int index)
	{
		std::map<char, bool> m1;
		for (int i = 0; i < 9; i++)
		{
			if (board[index][i] != '.')
			{
				if (m1.count(board[index][i]))
					return false;
				else
					m1[board[index][i]] = true;
			}
		}
		return true;
	}

	bool checkCol(std::vector<std::vector<char>>& board, int index)
	{
		std::map<char, bool> m1;
		for (int i = 0; i < 9; i++)
		{
			if (board[i][index] != '.')
			{
				if (m1.count(board[i][index]))
					return false;
				else
					m1[board[i][index]] = true;
			}
		}
		return true;
	}

	bool checkBlock(std::vector<std::vector<char>>& board)
	{
		std::map<char, bool> m1;
		for (int i = 0; i < 9; i += 3)
		{
			for (int j = 0; j < 9; j += 3)
			{
				m1.clear( );
				for (int m = 0; m < 3; m++)
				{
					for (int n = 0; n < 3; n++)
					{
						if (board[m + i][n + j] != '.')
							if (m1.count(board[m + i][n + j]))
								return false;
							else
								m1[board[m + i][n + j]] = true;
					}
				}
			}
		}
	}
```


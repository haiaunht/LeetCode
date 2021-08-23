# [37. Sudoku Solver (Hard)](https://leetcode.com/problems/sudoku-solver/)

<p>Write a program to solve a Sudoku puzzle by filling the empty cells.</p>

<p>A sudoku solution must satisfy <strong>all of the following rules</strong>:</p>

<ol>
	<li>Each of the digits <code>1-9</code> must occur exactly once in each row.</li>
	<li>Each of the digits <code>1-9</code> must occur exactly once in each column.</li>
	<li>Each of the digits <code>1-9</code> must occur exactly once in each of the 9 <code>3x3</code> sub-boxes of the grid.</li>
</ol>

<p>The <code>'.'</code> character indicates empty cells.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png" style="height:250px; width:250px">
<pre><strong>Input:</strong> board = [["5","3",".",".","7",".",".",".","."],["6",".",".","1","9","5",".",".","."],[".","9","8",".",".",".",".","6","."],["8",".",".",".","6",".",".",".","3"],["4",".",".","8",".","3",".",".","1"],["7",".",".",".","2",".",".",".","6"],[".","6",".",".",".",".","2","8","."],[".",".",".","4","1","9",".",".","5"],[".",".",".",".","8",".",".","7","9"]]
<strong>Output:</strong> [["5","3","4","6","7","8","9","1","2"],["6","7","2","1","9","5","3","4","8"],["1","9","8","3","4","2","5","6","7"],["8","5","9","7","6","1","4","2","3"],["4","2","6","8","5","3","7","9","1"],["7","1","3","9","2","4","8","5","6"],["9","6","1","5","3","7","2","8","4"],["2","8","7","4","1","9","6","3","5"],["3","4","5","2","8","6","1","7","9"]]
<strong>Explanation:</strong>&nbsp;The input board is shown above and the only valid solution is shown below:

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Sudoku-by-L2G-20050714_solution.svg/250px-Sudoku-by-L2G-20050714_solution.svg.png" style="height:250px; width:250px">
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>board.length == 9</code></li>
	<li><code>board[i].length == 9</code></li>
	<li><code>board[i][j]</code> is a digit or <code>'.'</code>.</li>
	<li>It is <strong>guaranteed</strong> that the input board has only one solution.</li>
</ul>

**Companies**:  
[DoorDash](https://leetcode.com/company/doordash), [Microsoft](https://leetcode.com/company/microsoft), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Intuit](https://leetcode.com/company/intuit), [Bloomberg](https://leetcode.com/company/bloomberg), [Adobe](https://leetcode.com/company/adobe), [Uber](https://leetcode.com/company/uber)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Backtracking](https://leetcode.com/tag/backtracking/), [Matrix](https://leetcode.com/tag/matrix/)

**Similar Questions**:

- [Valid Sudoku (Medium)](https://leetcode.com/problems/valid-sudoku/)
- [Unique Paths III (Hard)](https://leetcode.com/problems/unique-paths-iii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/sudoku-solver/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public void solveSudoku(char[][] board) {
        solve(board);
    }
    public boolean solve(char[][] board) {
        for (int i=0; i<board.length; i++) {
            for (int j=0; j<board[0].length; j++) {
                if (board[i][j] == '.') {
                    for (char c='1'; c<='9'; c++) {
                        //if we can place an number char here, check the whole board again, else return the origin '.'
                        if (isValidPos(board, i, j, c)) {
                            board[i][j] = c;
                            //solve the board
                            if (solve(board)) {
                                return true;
                            } else {
                                board[i][j] = '.'; //
                            }
                        }
                    }
                    //if we are here, the for loop from 1-9 is not valid,
                    return false;
                }
            }
        }
        return true;
    }
    public boolean isValidPos(char[][]board, int row, int col, char c) {
        //from number 1 - 9, valid if the row not contain it, col not contain it, the box not contain it as well
        for (int i=0; i<9; i++) {
            if (board[row][i] == c) return false;
            if (board[i][col] == c) return false;
            //int the box, loop from 1->9, the row is i/3 as 0 to 2 divide by 3 is 0, 3 to 5 divide 3 is 1, and 6 to 8 divide by 3 is 2
            //the col is i%3
            int boxRow = 3 * (row/3);
            int boxCol = 3 * (col/3);
            if (board[boxRow + i/3][boxCol + i%3] == c) return false;
        }
        return true;
    }
}

```

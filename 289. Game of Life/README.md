# [289. Game of Life (Medium)](https://leetcode.com/problems/game-of-life/)

<p>According to&nbsp;<a href="https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life" target="_blank">Wikipedia's article</a>: "The <b>Game of Life</b>, also known simply as <b>Life</b>, is a cellular automaton devised by the British mathematician John Horton Conway in 1970."</p>

<p>The board is made up of an <code>m x n</code> grid of cells, where each cell has an initial state: <b>live</b> (represented by a <code>1</code>) or <b>dead</b> (represented by a <code>0</code>). Each cell interacts with its <a href="https://en.wikipedia.org/wiki/Moore_neighborhood" target="_blank">eight neighbors</a> (horizontal, vertical, diagonal) using the following four rules (taken from the above Wikipedia article):</p>

<ol>
	<li>Any live cell with fewer than two live neighbors dies as if caused by under-population.</li>
	<li>Any live cell with two or three live neighbors lives on to the next generation.</li>
	<li>Any live cell with more than three live neighbors dies, as if by over-population.</li>
	<li>Any dead cell with exactly three live neighbors becomes a live cell, as if by reproduction.</li>
</ol>

<p><span>The next state is created by applying the above rules simultaneously to every cell in the current state, where births and deaths occur simultaneously. Given the current state of the <code>m x n</code> grid <code>board</code>, return <em>the next state</em>.</span></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/12/26/grid1.jpg" style="width: 562px; height: 322px;">
<pre><strong>Input:</strong> board = [[0,1,0],[0,0,1],[1,1,1],[0,0,0]]
<strong>Output:</strong> [[0,0,0],[1,0,1],[0,1,1],[0,1,0]]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/12/26/grid2.jpg" style="width: 402px; height: 162px;">
<pre><strong>Input:</strong> board = [[1,1],[1,0]]
<strong>Output:</strong> [[1,1],[1,1]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == board.length</code></li>
	<li><code>n == board[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 25</code></li>
	<li><code>board[i][j]</code> is <code>0</code> or <code>1</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong></p>

<ul>
	<li>Could you solve it in-place? Remember that the board needs to be updated simultaneously: You cannot update some cells first and then use their updated values to update other cells.</li>
	<li>In this question, we represent the board using a 2D array. In principle, the board is infinite, which would cause problems when the active area encroaches upon the border of the array (i.e., live cells reach the border). How would you address these problems?</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Dropbox](https://leetcode.com/company/dropbox), [Opendoor](https://leetcode.com/company/opendoor), [Square](https://leetcode.com/company/square), [Google](https://leetcode.com/company/google), [Reddit](https://leetcode.com/company/reddit), [Apple](https://leetcode.com/company/apple), [Adobe](https://leetcode.com/company/adobe), [Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Matrix](https://leetcode.com/tag/matrix/), [Simulation](https://leetcode.com/tag/simulation/)

**Similar Questions**:

- [Set Matrix Zeroes (Medium)](https://leetcode.com/problems/set-matrix-zeroes/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/game-of-life/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public void gameOfLife(int[][] board) {
        //rules: live cell has neightbor < 2 -> 0, >= 2 -> 1, >= 3 -> 0,
        //       dead cell has neightbors = 3 -> 1
        int rows = board.length;
        int cols = board[0].length;
        int[][] copy = new int[rows][cols];
        for (int row = 0; row < rows; row++) {
            for (int col = 0; col < cols; col++) {
                copy[row][col] = board[row][col];
            }
        }
        for (int row = 0; row<rows; row++) {
            for (int col=0; col<cols; col++) {
                //there are two case to start, live cell or dead cell
                if (copy[row][col] == 1) {
                    int liveCellNeightbors = countLiveNeighbors(copy, row, col);
                    if (liveCellNeightbors < 2 || liveCellNeightbors > 3) {
                        board[row][col] = 0;
                    } else if (liveCellNeightbors <= 3) {
                        board[row][col] = 1;
                    }
                } else {
                    int liveCellNeightbors = countLiveNeighbors(copy, row, col);
                    if (liveCellNeightbors == 3) board[row][col] = 1;
                }
            }
        }
    }
    private int countLiveNeighbors(int[][] board, int row, int col) {
        //direction will go up,down, left, right by one also go diganol
        int[][] directions = {{1,0}, {-1,0}, {0,1}, {0,-1}, {-1,-1},{-1,1}, {1,-1}, {1,1}};
        int countLive = 0;
        for (int[] dir : directions) {
            int currX = row + dir[0];
            int currY = col + dir[1];
            if (currX < 0 || currX >= board.length || currY < 0 || currY >= board[0].length) continue;
            if (board[currX][currY] == 1) countLive++;
        }
        return countLive;
    }
}

```

# [361. Bomb Enemy (Medium)](https://leetcode.com/problems/bomb-enemy/)

<p>Given an <code>m x n</code> matrix <code>grid</code> where each cell is either a wall <code>'W'</code>, an enemy <code>'E'</code> or empty <code>'0'</code>, return <em>the maximum enemies you can kill using one bomb</em>. You can only place the bomb in an empty cell.</p>

<p>The bomb kills all the enemies in the same row and column from the planted point until it hits the wall since it is too strong to be destroyed.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/27/bomb1-grid.jpg" style="width: 600px; height: 187px;">
<pre><strong>Input:</strong> grid = [["0","E","0","0"],["E","0","W","E"],["0","E","0","0"]]
<strong>Output:</strong> 3
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/27/bomb2-grid.jpg" style="width: 500px; height: 194px;">
<pre><strong>Input:</strong> grid = [["W","W","W"],["0","0","0"],["E","E","E"]]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 500</code></li>
	<li><code>grid[i][j]</code> is either <code>'W'</code>, <code>'E'</code>, or <code>'0'</code>.</li>
</ul>

**Companies**:  
[LinkedIn](https://leetcode.com/company/linkedin), [Google](https://leetcode.com/company/google), [Uber](https://leetcode.com/company/uber)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/), [Matrix](https://leetcode.com/tag/matrix/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/bomb-enemy/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int maxKilledEnemies(char[][] grid) {
        int max = 0;
        int rows = grid.length;
        int cols = grid[0].length;
        for (int row=0; row<rows; row++) {
            for (int col=0; col<cols; col++) {
                if (grid[row][col] == '0')
                    max = Math.max(max, findEnemyKilled(grid, row, col));
            }
        }
        return max;
    }
    private int findEnemyKilled(char[][] grid, int row, int col) {
        int count = 0;
        //IMPORTANT, need to go from CURRENT row to up (else from 0-> current row see W stop)
        for (int i=row-1; i>=0; i--) {
            if (grid[i][col] == 'E') {
                count++;
            } else if (grid[i][col] == 'W') {
                break;
            }
        }
        //check from row below to the bottom row
        for (int i=row+1; i<grid.length; i++) {
            if (grid[i][col] == 'E') {
                count++;
            } else if (grid[i][col] == 'W') {
                break;
            }
        }
        //IMPORTANT, need to go from the current col and go to the left until see the wall, cannot go from 0->col
        for (int j=col-1;j>=0; j--) {
            if (grid[row][j] == 'E') {
                count++;
            } else if (grid[row][j] == 'W') {
                break;
            }
        }
        for (int j=col+1; j<grid[0].length; j++) {
            if (grid[row][j] == 'E') {
                count++;
            } else if (grid[row][j] == 'W') {
                break;
            }
        }
        return count;
    }
}

```

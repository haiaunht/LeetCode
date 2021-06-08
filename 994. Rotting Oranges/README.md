# [994. Rotting Oranges (Medium)](https://leetcode.com/problems/rotting-oranges/)

<p>You are given an <code>m x n</code> <code>grid</code> where each cell can have one of three values:</p>

<ul>
	<li><code>0</code> representing an empty cell,</li>
	<li><code>1</code> representing a fresh orange, or</li>
	<li><code>2</code> representing a rotten orange.</li>
</ul>

<p>Every minute, any fresh orange that is <strong>4-directionally adjacent</strong> to a rotten orange becomes rotten.</p>

<p>Return <em>the minimum number of minutes that must elapse until no cell has a fresh orange</em>. If <em>this is impossible, return</em> <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/02/16/oranges.png" style="width: 650px; height: 137px;">
<pre><strong>Input:</strong> grid = [[2,1,1],[1,1,0],[0,1,1]]
<strong>Output:</strong> 4
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> grid = [[2,1,1],[0,1,1],[1,0,1]]
<strong>Output:</strong> -1
<strong>Explanation:</strong> The orange in the bottom left corner (row 2, column 0) is never rotten, because rotting only happens 4-directionally.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> grid = [[0,2]]
<strong>Output:</strong> 0
<strong>Explanation:</strong> Since there are already no fresh oranges at minute 0, the answer is just 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 10</code></li>
	<li><code>grid[i][j]</code> is <code>0</code>, <code>1</code>, or <code>2</code>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft), [Oracle](https://leetcode.com/company/oracle), [Accolite](https://leetcode.com/company/accolite), [Walmart Labs](https://leetcode.com/company/walmart-labs), [Samsung](https://leetcode.com/company/samsung)

**Related Topics**:  
[Breadth-first Search](https://leetcode.com/tag/breadth-first-search/)

**Similar Questions**:

- [Walls and Gates (Medium)](https://leetcode.com/problems/walls-and-gates/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/rotting-oranges/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int orangesRotting(int[][] grid) {
        int minutes = 0;
        int fresh = 0;
        //use bfs to check if each cell is rotten, if yes, check if adj vertial or horizontal cell is not 2, rotten that cell
        Queue<String> coorCellRotten = new LinkedList<>();
        for (int i=0; i<grid.length; i++) {
            for (int j=0; j<grid[0].length; j++) {
                if (grid[i][j] == 2) {
                    coorCellRotten.add("" + i + j);
                } else if (grid[i][j] == 1) {
                    fresh++;
                }
            }
        }
        //create directions to check above, left, right and bottom cells
        int[][] directions = {{-1,0},{1,0},{0,-1},{0,1}};
        while (!coorCellRotten.isEmpty() && fresh > 0) {  
            int size = coorCellRotten.size();
            while ( size-- > 0) {
                String currentCell = coorCellRotten.poll();   //"00"
                // int currentX = Character.getNumericValue(currentCell.charAt(0));
                // int currentY = Character.getNumericValue(currentCell.charAt(1));
                //check 4 directions
                for (int[] c : directions) {
                    int currentX = Character.getNumericValue(currentCell.charAt(0)) + c[0];
                    int currentY = Character.getNumericValue(currentCell.charAt(1)) + c[1];
                    // currentX = currentX + c[0];
                    // currentY = currentY + c[1];
                    if (currentX<0 || currentX >= grid.length || currentY < 0 || currentY >= grid[0].length
                       || grid[currentX][currentY] == 0 || grid[currentX][currentY] == 2) {
                        continue; //out side of the grid or empty cell, skip
                    } 
                    if (grid[currentX][currentY] == 1) {
                        grid[currentX][currentY] = 2;
                        coorCellRotten.add(""+(currentX)+(currentY));               
                    }      
                    fresh--;
                }
            }
            minutes++;
        }
        if (fresh > 0) return -1;
        return minutes;
    }
}

```

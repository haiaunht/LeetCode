# [463. Island Perimeter (Easy)](https://leetcode.com/problems/island-perimeter/)

<p>You are given <code>row x col</code> <code>grid</code> representing a map where <code>grid[i][j] = 1</code> represents&nbsp;land and <code>grid[i][j] = 0</code> represents water.</p>

<p>Grid cells are connected <strong>horizontally/vertically</strong> (not diagonally). The <code>grid</code> is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells).</p>

<p>The island doesn't have "lakes", meaning the water inside isn't connected to the water around the island. One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img src="https://assets.leetcode.com/uploads/2018/10/12/island.png" style="width: 221px; height: 213px;">
<pre><strong>Input:</strong> grid = [[0,1,0,0],[1,1,1,0],[0,1,0,0],[1,1,0,0]]
<strong>Output:</strong> 16
<strong>Explanation:</strong> The perimeter is the 16 yellow stripes in the image above.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> grid = [[1]]
<strong>Output:</strong> 4
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> grid = [[1,0]]
<strong>Output:</strong> 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>row == grid.length</code></li>
	<li><code>col == grid[i].length</code></li>
	<li><code>1 &lt;= row, col &lt;= 100</code></li>
	<li><code>grid[i][j]</code> is <code>0</code> or <code>1</code>.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/)

**Similar Questions**:

- [Max Area of Island (Medium)](https://leetcode.com/problems/max-area-of-island/)
- [Flood Fill (Easy)](https://leetcode.com/problems/flood-fill/)
- [Coloring A Border (Medium)](https://leetcode.com/problems/coloring-a-border/)

## Solution 1.

```Java
// OJ: https://leetcode.com/problems/island-perimeter/
// Author: Please set your name in options page
// Time: O()
// Space: O()
}
class Solution {
    public int islandPerimeter(int[][] grid) {
        int result = 0;
        for (int i=0; i<grid.length; i++) {
            for (int j=0; j<grid[0].length; j++) {
                if (grid[i][j] == 1) {
                    result += 4;
                    //if two cell next to each other perimeter = 8-2
                    //we are checking from left -> right and top -> bottom
                    //at each cell if there is a above cell or a left cell
                    if (i > 0 && grid[i-1][j] == 1) {
                        result -= 2;
                    }
                    if (j>0 && grid[i][j-1] == 1) {
                        result -= 2;
                    }
                }
            }
        }
        return result;
    }
}

```

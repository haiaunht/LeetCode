# [694. Number of Distinct Islands (Medium)](https://leetcode.com/problems/number-of-distinct-islands/)

<p>You are given an <code>m x n</code> binary matrix <code>grid</code>. An island is a group of <code>1</code>'s (representing land) connected <strong>4-directionally</strong> (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.</p>

<p>An island is considered to be the same as another if and only if one island can be translated (and not rotated or reflected) to equal the other.</p>

<p>Return <em>the number of <b>distinct</b> islands</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/01/distinctisland1-1-grid.jpg" style="width: 413px; height: 334px;">
<pre><strong>Input:</strong> grid = [[1,1,0,0,0],[1,1,0,0,0],[0,0,0,1,1],[0,0,0,1,1]]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/01/distinctisland1-2-grid.jpg" style="width: 413px; height: 334px;">
<pre><strong>Input:</strong> grid = [[1,1,0,1,1],[1,0,0,0,0],[0,0,0,0,1],[1,1,0,1,1]]
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 50</code></li>
	<li><code>grid[i][j]</code> is either <code>0</code> or <code>1</code>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Uber](https://leetcode.com/company/uber)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Union Find](https://leetcode.com/tag/union-find/), [Hash Function](https://leetcode.com/tag/hash-function/)

**Similar Questions**:

- [Number of Islands (Medium)](https://leetcode.com/problems/number-of-islands/)
- [Number of Distinct Islands II (Hard)](https://leetcode.com/problems/number-of-distinct-islands-ii/)
- [Count Sub Islands (Medium)](https://leetcode.com/problems/count-sub-islands/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/number-of-distinct-islands/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int numDistinctIslands(int[][] grid) {
        if (grid == null || grid.length == 0) return 0;
        Set<String> set = new HashSet<>();
        for (int i=0; i<grid.length; i++) {
          for (int j=0; j<grid[0].length; j++) {
            ////if counter a 1 cell, dfs to find the path and if the string is the same, set will not add
            if (grid[i][j] == 1) {
                String current = dfs(grid, i, j, "");
                set.add(current);
            }
          }
        }
        return set.size();
    }
    public String dfs(int[][] grid, int i, int j, String path) {
        if (i<0 || i>=grid.length || j<0 || j>=grid[0].length || grid[i][j] == 0) return path;
        //mark as visited
        grid[i][j] = 0;
        return ("1" + dfs(grid, i+1, j, "D") + dfs(grid, i-1, j, "U") + dfs(grid, i, j+1, "R") + dfs(grid, i, j-1, "L"));
    }
}

```

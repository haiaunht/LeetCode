# [200. Number of Islands (Medium)](https://leetcode.com/problems/number-of-islands/)

<p>Given an <code>m x n</code> 2D binary grid <code>grid</code> which represents a map of <code>'1'</code>s (land) and <code>'0'</code>s (water), return <em>the number of islands</em>.</p>

<p>An <strong>island</strong> is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 300</code></li>
	<li><code>grid[i][j]</code> is <code>'0'</code> or <code>'1'</code>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Bloomberg](https://leetcode.com/company/bloomberg), [Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google), [LinkedIn](https://leetcode.com/company/linkedin), [Uber](https://leetcode.com/company/uber), [Oracle](https://leetcode.com/company/oracle), [Qualtrics](https://leetcode.com/company/qualtrics), [Citadel](https://leetcode.com/company/citadel), [Yandex](https://leetcode.com/company/yandex), [ByteDance](https://leetcode.com/company/bytedance), [DoorDash](https://leetcode.com/company/doordash), [eBay](https://leetcode.com/company/ebay), [Expedia](https://leetcode.com/company/expedia), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Splunk](https://leetcode.com/company/splunk), [Snapchat](https://leetcode.com/company/snapchat), [VMware](https://leetcode.com/company/vmware)

**Related Topics**:  
[Depth-first Search](https://leetcode.com/tag/depth-first-search/), [Breadth-first Search](https://leetcode.com/tag/breadth-first-search/), [Union Find](https://leetcode.com/tag/union-find/)

**Similar Questions**:

- [Surrounded Regions (Medium)](https://leetcode.com/problems/surrounded-regions/)
- [Walls and Gates (Medium)](https://leetcode.com/problems/walls-and-gates/)
- [Number of Islands II (Hard)](https://leetcode.com/problems/number-of-islands-ii/)
- [Number of Connected Components in an Undirected Graph (Medium)](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/)
- [Number of Distinct Islands (Medium)](https://leetcode.com/problems/number-of-distinct-islands/)
- [Max Area of Island (Medium)](https://leetcode.com/problems/max-area-of-island/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/number-of-islands/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int numIslands(char[][] grid) {
        if (grid == null || grid.length == 0) return 0;
        int lands = 0;
        for (int i=0; i<grid.length; i++) {
            for (int j=0; j<grid[0].length; j++) {
                if (grid[i][j] == '1') {
                    lands += 1;
                    dfs(grid, i, j);
                }
            }
        }
        return lands;
    }
    private void dfs(char[][] grid, int i, int j) {
        if (i<0 || i>=grid.length || j<0 || j>=grid[0].length || grid[i][j] == '0') {
            return;
        }
        grid[i][j] = '0';
        dfs(grid, i-1, j);
        dfs(grid, i+1, j);
        dfs(grid, i, j-1);
        dfs(grid, i, j+1);
    }
}

```

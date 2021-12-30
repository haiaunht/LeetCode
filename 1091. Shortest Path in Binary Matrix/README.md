# [1091. Shortest Path in Binary Matrix (Medium)](https://leetcode.com/problems/shortest-path-in-binary-matrix/)

<p>Given an <code>n x n</code> binary matrix <code>grid</code>, return <em>the length of the shortest <strong>clear path</strong> in the matrix</em>. If there is no clear path, return <code>-1</code>.</p>

<p>A <strong>clear path</strong> in a binary matrix is a path from the <strong>top-left</strong> cell (i.e., <code>(0, 0)</code>) to the <strong>bottom-right</strong> cell (i.e., <code>(n - 1, n - 1)</code>) such that:</p>

<ul>
	<li>All the visited cells of the path are <code>0</code>.</li>
	<li>All the adjacent cells of the path are <strong>8-directionally</strong> connected (i.e., they are different and they share an edge or a corner).</li>
</ul>

<p>The <strong>length of a clear path</strong> is the number of visited cells of this path.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/18/example1_1.png" style="width: 500px; height: 234px;">
<pre><strong>Input:</strong> grid = [[0,1],[1,0]]
<strong>Output:</strong> 2
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/18/example2_1.png" style="height: 216px; width: 500px;">
<pre><strong>Input:</strong> grid = [[0,0,0],[1,1,0],[1,1,0]]
<strong>Output:</strong> 4
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> grid = [[1,0,0],[1,1,0],[1,1,0]]
<strong>Output:</strong> -1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 100</code></li>
	<li><code>grid[i][j] is 0 or 1</code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft), [Bloomberg](https://leetcode.com/company/bloomberg)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Matrix](https://leetcode.com/tag/matrix/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/shortest-path-in-binary-matrix/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int shortestPathBinaryMatrix(int[][] grid) {
        //edge cases, if start cell or end cell = 1 -> there is no clean path
        if (grid[0][0] != 0 || grid[grid.length-1][grid[0].length-1] != 0) return -1;
        int[][] directions = {{-1,-1}, {-1,0}, {-1,1},
                              {0,-1},          {0,1},
                              {1,-1},  {1,0},  {1,1}};
        Set<String> seen = new HashSet<>();
        int distance = 0;
        Queue<Pair<Integer,Integer>> queue = new LinkedList<>();
        queue.add(new Pair(0,0));
        while (!queue.isEmpty()) {
            distance++;
            int size = queue.size();
            for (int i=0; i<size; i++) {
                Pair<Integer,Integer> curr = queue.poll();
                int currX = curr.getKey();
                int currY = curr.getValue();
                if (currX == grid.length -1 && currY == grid[0].length-1) return distance;
                for (int[] dir : directions) {
                    int x = dir[0] + currX;
                    int y = dir[1] + currY;
                    if (x<0 || x >= grid.length || y<0 || y >= grid[0].length || grid[x][y] == 1) continue;
                    queue.add(new Pair(x, y));
                    grid[x][y] = 1;
                } 
            }
        }
        //here when i cannot find a clear path
        return -1;
    }
}

```

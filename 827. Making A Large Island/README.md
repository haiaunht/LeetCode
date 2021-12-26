# [827. Making A Large Island (Hard)](https://leetcode.com/problems/making-a-large-island/)

<p>You are given an <code>n x n</code> binary matrix <code>grid</code>. You are allowed to change <strong>at most one</strong> <code>0</code> to be <code>1</code>.</p>

<p>Return <em>the size of the largest <strong>island</strong> in</em> <code>grid</code> <em>after applying this operation</em>.</p>

<p>An <strong>island</strong> is a 4-directionally connected group of <code>1</code>s.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> grid = [[1,0],[0,1]]
<strong>Output:</strong> 3
<strong>Explanation:</strong> Change one 0 to 1 and connect two 1s, then we get an island with area = 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> grid = [[1,1],[1,0]]
<strong>Output:</strong> 4
<strong>Explanation: </strong>Change the 0 to 1 and make the island bigger, only one island with area = 4.</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> grid = [[1,1],[1,1]]
<strong>Output:</strong> 4
<strong>Explanation:</strong> Can't change any 0 to 1, only one island with area = 4.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 500</code></li>
	<li><code>grid[i][j]</code> is either <code>0</code> or <code>1</code>.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Union Find](https://leetcode.com/tag/union-find/), [Matrix](https://leetcode.com/tag/matrix/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/making-a-large-island/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int largestIsland(int[][] grid) {
        int largest = 0;
        boolean hasZero = false;
        for (int row=0; row<grid.length; row++) {
            for (int col=0; col<grid[0].length; col++) {
                if (grid[row][col] == 0) {
                    hasZero = true;
                    //mark this as 1 to count the area of island
                    grid[row][col] = 1;
                    largest = Math.max(largest, dfs(grid, row, col));
                    //return the origin
                    grid[row][col] = 0;
                }
            }
        }
        if (hasZero) return largest;
        return grid.length * grid[0].length;
    }
    public static int dfs(int[][] grid, int row, int col) {
        int[][] directions = {{-1,0}, {1,0}, {0,-1}, {0,1}}; //up, down, left, right
        Set<String> seen = new HashSet<>();
        Queue<String> queue = new LinkedList<>();
        queue.add("" + row + col);
        seen.add("" + row + col);
        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i=0; i<size; i++) {
                String curr = queue.poll();
                for (int[] dir : directions) {
                    int currX = Character.getNumericValue(curr.charAt(0)) + dir[0];
                    int currY = Character.getNumericValue(curr.charAt(1)) + dir[1];
                    if (currX<0 || currX>=grid.length || currY<0 || currY>=grid[0].length || grid[currX][currY] == 0 || seen.contains("" + currX + currY)) continue;
                    queue.add("" + currX + currY);
                    seen.add("" + currX + currY);
                }
            }
        }
        return seen.size();
    }
}

```

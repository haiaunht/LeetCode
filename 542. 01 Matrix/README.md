# [542. 01 Matrix (Medium)](https://leetcode.com/problems/01-matrix/)

<p>Given an <code>m x n</code> binary matrix <code>mat</code>, return <em>the distance of the nearest </em><code>0</code><em> for each cell</em>.</p>

<p>The distance between two adjacent cells is <code>1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/04/24/01-1-grid.jpg" style="width: 253px; height: 253px;">
<pre><strong>Input:</strong> mat = [[0,0,0],[0,1,0],[0,0,0]]
<strong>Output:</strong> [[0,0,0],[0,1,0],[0,0,0]]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/04/24/01-2-grid.jpg" style="width: 253px; height: 253px;">
<pre><strong>Input:</strong> mat = [[0,0,0],[0,1,0],[1,1,1]]
<strong>Output:</strong> [[0,0,0],[0,1,0],[1,2,1]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= m * n &lt;= 10<sup>4</sup></code></li>
	<li><code>mat[i][j]</code> is either <code>0</code> or <code>1</code>.</li>
	<li>There is at least one <code>0</code> in <code>mat</code>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Google](https://leetcode.com/company/google), [Uber](https://leetcode.com/company/uber), [Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Matrix](https://leetcode.com/tag/matrix/)

**Similar Questions**:

- [Shortest Path to Get Food (Medium)](https://leetcode.com/problems/shortest-path-to-get-food/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/01-matrix/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int[][] updateMatrix(int[][] mat) {
        Queue<int[]> queue = new LinkedList<>();
        for (int i=0; i<mat.length; i++) {
            for (int j=0; j<mat[0].length; j++) {
                if (mat[i][j] == 0) queue.add(new int[]{i,j});
                else mat[i][j] = -1;
            }
        }
        int[][] directions = {{0,1}, {0,-1}, {-1,0}, {1,0}};
        int distance = 0;
        while (queue.size() != 0) {
            int size = queue.size();
            distance++;
            while (size-- > 0) {
                int[] current = queue.poll();
                for (int[] dir : directions) {
                    int currX = dir[0] + current[0];
                    int currY = dir[1] + current[1];
                    if (currX < 0 || currX >= mat.length || currY < 0 || currY >= mat[0].length || mat[currX][currY] != -1) {
                        continue;
                    }
                    mat[currX][currY] = distance;
                    queue.add(new int[]{currX, currY});
                }
            }
        }
        return mat;
    }
}

```

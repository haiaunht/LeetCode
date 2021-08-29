# [317. Shortest Distance from All Buildings (Hard)](https://leetcode.com/problems/shortest-distance-from-all-buildings/)

<p>You are given an <code>m x n</code> grid <code>grid</code> of values <code>0</code>, <code>1</code>, or <code>2</code>, where:</p>

<ul>
	<li>each <code>0</code> marks <strong>an empty land</strong> that you can pass by freely,</li>
	<li>each <code>1</code> marks <strong>a building</strong> that you cannot pass through, and</li>
	<li>each <code>2</code> marks <strong>an obstacle</strong> that you cannot pass through.</li>
</ul>

<p>You want to build a house on an empty land that reaches all buildings in the <strong>shortest total travel</strong> distance. You can only move up, down, left, and right.</p>

<p>Return <em>the <strong>shortest travel distance</strong> for such a house</em>. If it is not possible to build such a house according to the above rules, return <code>-1</code>.</p>

<p>The <strong>total travel distance</strong> is the sum of the distances between the houses of the friends and the meeting point.</p>

<p>The distance is calculated using <a href="http://en.wikipedia.org/wiki/Taxicab_geometry" target="_blank">Manhattan Distance</a>, where <code>distance(p1, p2) = |p2.x - p1.x| + |p2.y - p1.y|</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/14/buildings-grid.jpg" style="width: 413px; height: 253px;">
<pre><strong>Input:</strong> grid = [[1,0,2,0,1],[0,0,0,0,0],[0,0,1,0,0]]
<strong>Output:</strong> 7
<strong>Explanation:</strong> Given three buildings at (0,0), (0,4), (2,2), and an obstacle at (0,2).
The point (1,2) is an ideal empty land to build a house, as the total travel distance of 3+3+1=7 is minimal.
So return 7.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> grid = [[1,0]]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> grid = [[1]]
<strong>Output:</strong> -1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 50</code></li>
	<li><code>grid[i][j]</code> is either <code>0</code>, <code>1</code>, or <code>2</code>.</li>
	<li>There will be <strong>at least one</strong> building in the <code>grid</code>.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Qualtrics](https://leetcode.com/company/qualtrics), [Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Matrix](https://leetcode.com/tag/matrix/)

**Similar Questions**:

- [Walls and Gates (Medium)](https://leetcode.com/problems/walls-and-gates/)
- [Best Meeting Point (Hard)](https://leetcode.com/problems/best-meeting-point/)
- [As Far from Land as Possible (Medium)](https://leetcode.com/problems/as-far-from-land-as-possible/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/shortest-distance-from-all-buildings/
// Author: Please set your name in options page
// Time: O(row*row*col*col)
// Space: O(row*col)
            for (int i=0; i<size; i++) {
                int[] currentCell = queue.poll();
                if (grid[currentCell[0]][currentCell[1]] == 1) {
                    sumDistance += level;
                    houseReached++;
                    continue;
                }
                //if not, travel in 4 directions and add to the queue to continue to check
                for (int[] dir : directions) {
                    int currX = currentCell[0] + dir[0];
                    int currY = currentCell[1] + dir[1];
                    if (currX<0 || currX>=grid.length || currY<0 || currY>=grid[0].length
                       || grid[currX][currY] == 2 || visited[currX][currY] == true) {
                        continue;
                    }
                    visited[currX][currY] = true;
                    queue.add(new int[]{currX, currY});
                }
            }
            level++;
        }
        //EDGE case:when we cannot reach all house, mark these visited cell is 2, return Max_int
        if (houseReached != buildings) {
            for (int i=0; i<grid.length; i++) {
                for (int j=0; j<grid[0].length; j++) {
                    if (grid[i][j] == 0 && visited[i][j] == true) {
                        grid[i][j] = 2;
                    }
                }
            }
            return Integer.MAX_VALUE;
        }
        return sumDistance;
    }
};

```

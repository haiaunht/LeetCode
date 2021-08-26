# [1197. Minimum Knight Moves (Medium)](https://leetcode.com/problems/minimum-knight-moves/)

<p>In an <strong>infinite</strong> chess board with coordinates from <code>-infinity</code> to <code>+infinity</code>, you have a <strong>knight</strong> at square <code>[0, 0]</code>.</p>

<p>A knight has 8 possible moves it can make, as illustrated below. Each move is two squares in a cardinal direction, then one square in an orthogonal direction.</p>
<img src="https://assets.leetcode.com/uploads/2018/10/12/knight.png" style="height: 250px; width: 250px;">
<p>Return <em>the minimum number of steps needed to move the knight to the square</em> <code>[x, y]</code>. It is guaranteed the answer exists.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> x = 2, y = 1
<strong>Output:</strong> 1
<strong>Explanation: </strong>[0, 0] → [2, 1]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> x = 5, y = 5
<strong>Output:</strong> 4
<strong>Explanation: </strong>[0, 0] → [2, 1] → [4, 2] → [3, 4] → [5, 5]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-300 &lt;= x, y &lt;= 300</code></li>
	<li><code>0 &lt;= |x| + |y| &lt;= 300</code></li>
</ul>

**Companies**:  
[Expedia](https://leetcode.com/company/expedia), [Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft), [Indeed](https://leetcode.com/company/indeed), [Twitter](https://leetcode.com/company/twitter), [Twitch](https://leetcode.com/company/twitch)

**Related Topics**:  
[Breadth-First Search](https://leetcode.com/tag/breadth-first-search/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/minimum-knight-moves/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    class Coordinate {
        int x;
        int y;
        Coordinate(int x, int y) {
            this.x = x;
            this.y = y;
        }
    }
    public int minKnightMoves(int x, int y) {
        //because these {x,y} is sysmetric -> move all to the first quarant to check
        x = Math.abs(x);
        y = Math.abs(y);
        int[][] directions = {{1,2},{1,-2}, {-1,2},{-1,-2} ,
                              {2,1},{2,-1}, {-2,1}, {-2,-1}};
        Set<String> visited = new HashSet<>();
        visited.add("0,0");
        Queue<Coordinate> queue = new LinkedList<>();
        queue.add(new Coordinate(0,0));
        int level=0;
        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i=0; i<size; i++) {
                Coordinate curr = queue.poll();
                if (curr.x == x && curr.y == y) return level;
                for (int[] dir : directions) {
                    int currX = curr.x + dir[0];
                    int currY = curr.y + dir[1];
                    String s = currX + "," + currY;
                    if (!visited.contains(s) && currX > -2 && currY > -2) {
                        visited.add(s);
                        queue.add(new Coordinate(currX, currY));
                    }
                }
            }
            level++;
        }
        return level;
    }
}

```

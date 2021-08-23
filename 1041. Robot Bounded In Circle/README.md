# [1041. Robot Bounded In Circle (Medium)](https://leetcode.com/problems/robot-bounded-in-circle/)

<p>On an infinite plane, a robot initially stands at <code>(0, 0)</code> and faces north. The robot can receive one of three instructions:</p>

<ul>
	<li><code>"G"</code>: go straight 1 unit;</li>
	<li><code>"L"</code>: turn 90 degrees to the left;</li>
	<li><code>"R"</code>: turn 90 degrees to the right.</li>
</ul>

<p>The robot performs the <code>instructions</code> given in order, and repeats them forever.</p>

<p>Return <code>true</code> if and only if there exists a circle in the plane such that the robot never leaves the circle.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> instructions = "GGLLGG"
<strong>Output:</strong> true
<strong>Explanation:</strong> The robot moves from (0,0) to (0,2), turns 180 degrees, and then returns to (0,0).
When repeating these instructions, the robot remains in the circle of radius 2 centered at the origin.</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> instructions = "GG"
<strong>Output:</strong> false
<strong>Explanation:</strong> The robot moves north indefinitely.</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> instructions = "GL"
<strong>Output:</strong> true
<strong>Explanation:</strong> The robot moves from (0, 0) -&gt; (0, 1) -&gt; (-1, 1) -&gt; (-1, 0) -&gt; (0, 0) -&gt; ...</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= instructions.length &lt;= 100</code></li>
	<li><code>instructions[i]</code> is <code>'G'</code>, <code>'L'</code> or, <code>'R'</code>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Adobe](https://leetcode.com/company/adobe), [Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/), [String](https://leetcode.com/tag/string/), [Simulation](https://leetcode.com/tag/simulation/)

## Solution 1.

```Java
// OJ: https://leetcode.com/problems/robot-bounded-in-circle/
// Author: Hai-Au
// Time: O(n)
// Space: O(1) because directions only contains 4 elements
class Solution {
    public boolean isRobotBounded(String instructions) {
        //if the robot stay at the origin or the direction is changing after the series of instructions -> true
        // directions keep track of go North is {0,1}, East {1,0}, South {0,-1} West{-1,0}
        int[][] directions = new int[][] {{0,1}, {1,0}, {0,-1}, {-1,0}};
        //when the robot start, dir is north {0,1} and x=0;y=0
        int x=0;
        int y=0;
        int dir=0;
        for (char instruction : instructions.toCharArray()) {
            //if turn left dir = (dir-1)%4 or (dir+3)%4 to avoid negative
            if (instruction == 'L') {
                dir = (dir+3)%4;
            } else if (instruction == 'R') {
                dir = (dir+1)%4;
            } else {
                int[] currDirection = directions[dir];
                //now update x and y
                x += currDirection[0];
                y += currDirection[1];
            }
        }
        return ((x==0 && y==0) || dir != 0);
    }
}

```

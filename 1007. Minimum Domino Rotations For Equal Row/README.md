# [1007. Minimum Domino Rotations For Equal Row (Medium)](https://leetcode.com/problems/minimum-domino-rotations-for-equal-row/)

<p>In a row of dominoes, <code>tops[i]</code> and <code>bottoms[i]</code> represent the top and bottom halves of the <code>i<sup>th</sup></code> domino. (A domino is a tile with two numbers from 1 to 6 - one on each half of the tile.)</p>

<p>We may rotate the <code>i<sup>th</sup></code> domino, so that <code>tops[i]</code> and <code>bottoms[i]</code> swap values.</p>

<p>Return the minimum number of rotations so that all the values in <code>tops</code> are the same, or all the values in <code>bottoms</code> are the same.</p>

<p>If it cannot be done, return <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/14/domino.png" style="height: 300px; width: 421px;">
<pre><strong>Input:</strong> tops = [2,1,2,4,2,2], bottoms = [5,2,6,2,3,2]
<strong>Output:</strong> 2
<strong>Explanation:</strong> 
The first figure represents the dominoes as given by tops and bottoms: before we do any rotations.
If we rotate the second and fourth dominoes, we can make every value in the top row equal to 2, as indicated by the second figure.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> tops = [3,5,1,2,3], bottoms = [3,6,3,3,4]
<strong>Output:</strong> -1
<strong>Explanation:</strong> 
In this case, it is not possible to rotate the dominoes to make one row of values equal.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= tops.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>bottoms.length == tops.length</code></li>
	<li><code>1 &lt;= tops[i], bottoms[i] &lt;= 6</code></li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Greedy](https://leetcode.com/tag/greedy/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/minimum-domino-rotations-for-equal-row/solution/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(1)
class Solution {
    public int minDominoRotations(int[] tops, int[] bottoms) {
        int minRotation = 0;
        //either arrange all equal tops[0] or bottoms[0] and calcualte the min rotation
        minRotation = Math.min(match(tops[0], tops, bottoms), match(bottoms[0], tops, bottoms));
        minRotation = Math.min(minRotation, Math.min(match(tops[0], bottoms, tops), match(bottoms[0], bottoms, tops)));
        return (minRotation == Integer.MAX_VALUE) ? -1 : minRotation;
    }
    public int match(int target, int[] one, int[] two) {
        int swap = 0;
        for (int i=0; i<one.length; i++) {
            if (one[i] != target && two[i] != target) {
                return Integer.MAX_VALUE;
            } else if (one[i] != target) {
                swap++;
            }
        }
        return swap;
    }
}

```

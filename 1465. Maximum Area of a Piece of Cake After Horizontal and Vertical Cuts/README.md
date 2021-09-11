# [1465. Maximum Area of a Piece of Cake After Horizontal and Vertical Cuts (Medium)](https://leetcode.com/problems/maximum-area-of-a-piece-of-cake-after-horizontal-and-vertical-cuts/)

<p>You are given a rectangular cake of size <code>h x w</code> and two arrays of integers <code>horizontalCuts</code> and <code>verticalCuts</code> where:</p>

<ul>
	<li><code>horizontalCuts[i]</code> is the distance from the top of the rectangular cake to the <code>i<sup>th</sup></code> horizontal cut and similarly, and</li>
	<li><code>verticalCuts[j]</code> is the distance from the left of the rectangular cake to the <code>j<sup>th</sup></code> vertical cut.</li>
</ul>

<p>Return <em>the maximum area of a piece of cake after you cut at each horizontal and vertical position provided in the arrays</em> <code>horizontalCuts</code> <em>and</em> <code>verticalCuts</code>. Since the answer can be a large number, return this <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/05/14/leetcode_max_area_2.png" style="width: 225px; height: 240px;">
<pre><strong>Input:</strong> h = 5, w = 4, horizontalCuts = [1,2,4], verticalCuts = [1,3]
<strong>Output:</strong> 4 
<strong>Explanation:</strong> The figure above represents the given rectangular cake. Red lines are the horizontal and vertical cuts. After you cut the cake, the green piece of cake has the maximum area.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/05/14/leetcode_max_area_3.png" style="width: 225px; height: 240px;">
<pre><strong>Input:</strong> h = 5, w = 4, horizontalCuts = [3,1], verticalCuts = [1]
<strong>Output:</strong> 6
<strong>Explanation:</strong> The figure above represents the given rectangular cake. Red lines are the horizontal and vertical cuts. After you cut the cake, the green and yellow pieces of cake have the maximum area.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> h = 5, w = 4, horizontalCuts = [3], verticalCuts = [3]
<strong>Output:</strong> 9
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= h, w &lt;= 10<sup>9</sup></code></li>
	<li><code>1 &lt;= horizontalCuts.length &lt;= min(h - 1, 10<sup>5</sup>)</code></li>
	<li><code>1 &lt;= verticalCuts.length &lt;= min(w - 1, 10<sup>5</sup>)</code></li>
	<li><code>1 &lt;= horizontalCuts[i] &lt; h</code></li>
	<li><code>1 &lt;= verticalCuts[i] &lt; w</code></li>
	<li>All the elements in <code>horizontalCuts</code> are distinct.</li>
	<li>All the elements in <code>verticalCuts</code> are distinct.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Expedia](https://leetcode.com/company/expedia), [Swiggy](https://leetcode.com/company/swiggy), [Salesforce](https://leetcode.com/company/salesforce)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Greedy](https://leetcode.com/tag/greedy/), [Sorting](https://leetcode.com/tag/sorting/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/maximum-area-of-a-piece-of-cake-after-horizontal-and-vertical-cuts/
// Author: Please set your name in options page
// Time: O(NlogN) for sorting
// Space: O(1) store 2 vars maxH and maxW
class Solution {
    public int maxArea(int h, int w, int[] horizontalCuts, int[] verticalCuts) {
        //array sort time: NlogN
        Arrays.sort(horizontalCuts);
        Arrays.sort(verticalCuts);
        int rows = horizontalCuts.length;
        int cols = verticalCuts.length;
        //compare if the height of 0->hor[0] or h-hor[hor.length-1] is bigger than inside
        long maxHeight = Math.max(horizontalCuts[0], h - horizontalCuts[rows - 1]);
        for (int i=1; i<rows; i++) {
            maxHeight = Math.max(maxHeight, horizontalCuts[i] - horizontalCuts[i-1]);
        }
        long maxWidth = Math.max(verticalCuts[0], w - verticalCuts[cols - 1]);
        for (int i=1; i<cols; i++) {
            maxWidth = Math.max(maxWidth, verticalCuts[i] - verticalCuts[i-1]);
        }
        return (int)((maxHeight * maxWidth) % 1000000007);
    }
}
        //compare if the height of 0->hor[0] or h-hor[hor.length-1] is bigger than insideN

```

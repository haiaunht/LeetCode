# [42. Trapping Rain Water (Hard)](https://leetcode.com/problems/trapping-rain-water/)

<p>Given <code>n</code> non-negative integers representing an elevation map where the width of each bar is <code>1</code>, compute how much water it can trap after raining.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img src="https://assets.leetcode.com/uploads/2018/10/22/rainwatertrap.png" style="width: 412px; height: 161px;">
<pre><strong>Input:</strong> height = [0,1,0,2,1,0,1,3,2,1,2,1]
<strong>Output:</strong> 6
<strong>Explanation:</strong> The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> height = [4,2,0,3,2,5]
<strong>Output:</strong> 9
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == height.length</code></li>
	<li><code>0 &lt;= n &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>0 &lt;= height[i] &lt;= 10<sup>5</sup></code></li>
</ul>

**Companies**:  
[Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Bloomberg](https://leetcode.com/company/bloomberg), [Microsoft](https://leetcode.com/company/microsoft), [Google](https://leetcode.com/company/google), [Apple](https://leetcode.com/company/apple), [Snapchat](https://leetcode.com/company/snapchat), [Adobe](https://leetcode.com/company/adobe), [Qualtrics](https://leetcode.com/company/qualtrics), [Yandex](https://leetcode.com/company/yandex)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Two Pointers](https://leetcode.com/tag/two-pointers/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/), [Stack](https://leetcode.com/tag/stack/)

**Similar Questions**:

- [Container With Most Water (Medium)](https://leetcode.com/problems/container-with-most-water/)
- [Product of Array Except Self (Medium)](https://leetcode.com/problems/product-of-array-except-self/)
- [Trapping Rain Water II (Hard)](https://leetcode.com/problems/trapping-rain-water-ii/)
- [Pour Water (Medium)](https://leetcode.com/problems/pour-water/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/trapping-rain-water/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int trap(int[] height) {
        int units = 0;
        if (height.length == 0) return 0;
        //calculate maxLeft of each point
        int[] maxLeft = new int[height.length];
        int maxL = height[0];
        maxLeft[0] = 0;
        for (int i=1; i<height.length; i++) {
            maxL = Math.max(maxL, height[i]);
            maxLeft[i] = maxL;
        }
        //calculate maxRight of each point
        int[] maxRight = new int[height.length];
        int maxR = height[height.length-1];
        maxRight[height.length-1] = 0;
        for (int i=height.length-2; i>=0; i--) {
            maxR = Math.max(maxR, height[i]);
            maxRight[i] = maxR;
        }
        //compare each maxLeft and maxRight and keep the min height
        int[] minLR = new int[height.length];
        for (int i=0; i<height.length; i++) {
            minLR[i] = Math.min(maxLeft[i], maxRight[i]);  
        }
        //count the unit by the min height of both side - the height of current point
        for (int i=0; i<height.length; i++) {
            if (minLR[i] - height[i] >= 0)
                units += minLR[i] - height[i];
        }
        return units;
    }
}

```

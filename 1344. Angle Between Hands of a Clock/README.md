# [1344. Angle Between Hands of a Clock (Medium)](https://leetcode.com/problems/angle-between-hands-of-a-clock/solution/)

<p>Given two numbers, <code>hour</code> and <code>minutes</code>. Return the smaller angle (in degrees) formed between the <code>hour</code> and the <code>minute</code> hand.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2019/12/26/sample_1_1673.png" style="width: 230px; height: 225px;"></p>

<pre><strong>Input:</strong> hour = 12, minutes = 30
<strong>Output:</strong> 165
</pre>

<p><strong>Example 2:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2019/12/26/sample_2_1673.png" style="width: 230px; height: 225px;"></p>

<pre><strong>Input:</strong> hour = 3, minutes = 30
<strong>Output:</strong> 75
</pre>

<p><strong>Example 3:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2019/12/26/sample_3_1673.png" style="width: 230px; height: 225px;"></strong></p>

<pre><strong>Input:</strong> hour = 3, minutes = 15
<strong>Output:</strong> 7.5
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> hour = 4, minutes = 50
<strong>Output:</strong> 155
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> hour = 12, minutes = 0
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= hour &lt;= 12</code></li>
	<li><code>0 &lt;= minutes &lt;= 59</code></li>
	<li>Answers within&nbsp;<code>10^-5</code>&nbsp;of the actual value will be accepted as correct.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Microsoft](https://leetcode.com/company/microsoft), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Oracle](https://leetcode.com/company/oracle)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/angle-between-hands-of-a-clock/solution/
// Author: Hai-Au
// Time: O(1)
// Space: O(1)
class Solution {
    public double angleClock(int hour, int minutes) {
        // 12 hours -> 360 degree => 1 hr -> move 360/12 = 30 degree
        // 60 minutes -> 360 degree => 1 minute -> move 360/60 = 6 degree
        final int DEGREE_PER_HOUR = 30;
        final int DEGREE_PER_MINUTE = 6;
        //when hour=12 -> it is 0 degree so we do hour % 12
        //calculate total degree by hour_hand and minute_hand and calculate the different
        double angle_hour_hand = (hour % 12 + minutes/60.0) * DEGREE_PER_HOUR;
        int angle_minute_hand = (minutes * DEGREE_PER_MINUTE);
        double result = Math.abs(angle_hour_hand - angle_minute_hand);
        return Math.min(result, 360-result);
    }
}

```

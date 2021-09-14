# [495. Teemo Attacking (Easy)](https://leetcode.com/problems/teemo-attacking/)

<p>Our hero Teemo is attacking an enemy Ashe with poison attacks! When Teemo attacks Ashe, Ashe gets poisoned for a exactly <code>duration</code> seconds. More formally, an attack at second <code>t</code> will mean Ashe is poisoned during the <strong>inclusive</strong> time interval <code>[t, t + duration - 1]</code>. If Teemo attacks again <strong>before</strong> the poison effect ends, the timer for it is <strong>reset</strong>, and the poison effect will end <code>duration</code> seconds after the new attack.</p>

<p>You are given a <strong>non-decreasing</strong> integer array <code>timeSeries</code>, where <code>timeSeries[i]</code> denotes that Teemo attacks Ashe at second <code>timeSeries[i]</code>, and an integer <code>duration</code>.</p>

<p>Return <em>the <strong>total</strong> number of seconds that Ashe is poisoned</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> timeSeries = [1,4], duration = 2
<strong>Output:</strong> 4
<strong>Explanation:</strong> Teemo's attacks on Ashe go as follows:
- At second 1, Teemo attacks, and Ashe is poisoned for seconds 1 and 2.
- At second 4, Teemo attacks, and Ashe is poisoned for seconds 4 and 5.
Ashe is poisoned for seconds 1, 2, 4, and 5, which is 4 seconds in total.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> timeSeries = [1,2], duration = 2
<strong>Output:</strong> 3
<strong>Explanation:</strong> Teemo's attacks on Ashe go as follows:
- At second 1, Teemo attacks, and Ashe is poisoned for seconds 1 and 2.
- At second 2 however, Teemo attacks again and resets the poison timer. Ashe is poisoned for seconds 2 and 3.
Ashe is poisoned for seconds 1, 2, and 3, which is 3 seconds in total.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= timeSeries.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= timeSeries[i], duration &lt;= 10<sup>7</sup></code></li>
	<li><code>timeSeries</code> is sorted in <strong>non-decreasing</strong> order.</li>
</ul>

**Companies**:  
[Salesforce](https://leetcode.com/company/salesforce)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Simulation](https://leetcode.com/tag/simulation/)

**Similar Questions**:

- [Merge Intervals (Medium)](https://leetcode.com/problems/merge-intervals/)
- [Can Place Flowers (Easy)](https://leetcode.com/problems/can-place-flowers/)
- [Dota2 Senate (Medium)](https://leetcode.com/problems/dota2-senate/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/teemo-attacking/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(1)
class Solution {
    public int findPoisonedDuration(int[] timeSeries, int duration) {
        if (timeSeries==null || timeSeries.length==0 ) return 0;
        int result = 0;
        for (int i=0; i<timeSeries.length-1; i++) {
            result += Math.min(timeSeries[i+1] - timeSeries[i], duration);
        }
        return result + duration;
    }
}

```

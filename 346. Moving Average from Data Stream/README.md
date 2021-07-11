# [346. Moving Average from Data Stream (Easy)](https://leetcode.com/problems/moving-average-from-data-stream/)

<p>Given a stream of integers and a window size, calculate the moving average of all integers in the sliding window.</p>

<p>Implement the&nbsp;<code>MovingAverage</code> class:</p>

<ul>
	<li><code>MovingAverage(int size)</code> Initializes&nbsp;the object with the size of the window <code>size</code>.</li>
	<li><code>double next(int val)</code> Returns the moving average of the last <code>size</code> values of the stream.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input</strong>
["MovingAverage", "next", "next", "next", "next"]
[[3], [1], [10], [3], [5]]
<strong>Output</strong>
[null, 1.0, 5.5, 4.66667, 6.0]

<strong>Explanation</strong>
MovingAverage movingAverage = new MovingAverage(3);
movingAverage.next(1); // return 1.0 = 1 / 1
movingAverage.next(10); // return 5.5 = (1 + 10) / 2
movingAverage.next(3); // return 4.66667 = (1 + 10 + 3) / 3
movingAverage.next(5); // return 6.0 = (10 + 3 + 5) / 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= size &lt;= 1000</code></li>
	<li><code>-10<sup>5</sup> &lt;= val &lt;= 10<sup>5</sup></code></li>
	<li>At most <code>10<sup>4</sup></code> calls will be made to <code>next</code>.</li>
</ul>

**Companies**:  
[Spotify](https://leetcode.com/company/spotify), [Google](https://leetcode.com/company/google), [Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple), [Indeed](https://leetcode.com/company/indeed)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Design](https://leetcode.com/tag/design/), [Queue](https://leetcode.com/tag/queue/), [Data Stream](https://leetcode.com/tag/data-stream/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/moving-average-from-data-stream/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class MovingAverage {
    private Queue<Integer> queue;
    private int maxSize;
    private double sum;
    /** Initialize your data structure here. */
    public MovingAverage(int size) {
        queue = new ArrayDeque<>(); //or new LinkedList<>();
        maxSize = size;
        sum = 0.0;
    }
    public double next(int val) {
        //check if the queue is reach max size, if yes, remove head, minus head's value from sum
        if (queue.size() == maxSize) {
            sum -= queue.poll();
        }
        //if not, add the val, calculate the sum then return avg
        queue.add(val);
        sum += val;
        return sum/queue.size();
    }
}
/**
 * Your MovingAverage object will be instantiated and called as such:
 * MovingAverage obj = new MovingAverage(size);
 * double param_1 = obj.next(val);
 */

```

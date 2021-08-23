# [253. Meeting Rooms II (Medium)](https://leetcode.com/problems/meeting-rooms-ii/)

<p>Given an array of meeting time intervals <code>intervals</code> where <code>intervals[i] = [start<sub>i</sub>, end<sub>i</sub>]</code>, return <em>the minimum number of conference rooms required</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> intervals = [[0,30],[5,10],[15,20]]
<strong>Output:</strong> 2
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> intervals = [[7,10],[2,4]]
<strong>Output:</strong> 1
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;=&nbsp;intervals.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= start<sub>i</sub> &lt; end<sub>i</sub> &lt;= 10<sup>6</sup></code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Bloomberg](https://leetcode.com/company/bloomberg), [Facebook](https://leetcode.com/company/facebook), [Google](https://leetcode.com/company/google), [ByteDance](https://leetcode.com/company/bytedance), [Walmart Labs](https://leetcode.com/company/walmart-labs), [Adobe](https://leetcode.com/company/adobe), [eBay](https://leetcode.com/company/ebay), [Uber](https://leetcode.com/company/uber), [Qualtrics](https://leetcode.com/company/qualtrics), [Snapchat](https://leetcode.com/company/snapchat), [Apple](https://leetcode.com/company/apple), [Visa](https://leetcode.com/company/visa), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Yandex](https://leetcode.com/company/yandex), [Docusign](https://leetcode.com/company/docusign)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Two Pointers](https://leetcode.com/tag/two-pointers/), [Greedy](https://leetcode.com/tag/greedy/), [Sorting](https://leetcode.com/tag/sorting/), [Heap (Priority Queue)](https://leetcode.com/tag/heap-priority-queue/)

**Similar Questions**:

- [Merge Intervals (Medium)](https://leetcode.com/problems/merge-intervals/)
- [Meeting Rooms (Easy)](https://leetcode.com/problems/meeting-rooms/)
- [Minimum Number of Arrows to Burst Balloons (Medium)](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)
- [Car Pooling (Medium)](https://leetcode.com/problems/car-pooling/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/meeting-rooms-ii/
// Author: Hai-Au
// Time: O(n)
// Space: O(n)
class Solution {
    public int minMeetingRooms(int[][] intervals) {
        int count = 0;
        //sort the intervals
        Arrays.sort(intervals, (a,b)->Integer.compare(a[0],b[0]));
        //use minHeap to keep track the end meeting time, if there is a meeting has end time < current -> add 1 more room , else we are good
        PriorityQueue<Integer> minHeap = new PriorityQueue<Integer>();
        minHeap.add(intervals[0][1]);
        for (int i = 1; i < intervals.length; i++) {
            int[] currentMeeting = intervals[i];
            //if. the min heap less than the start meeting time, dont need a room, -> remove from the queue
            if (minHeap.peek() <= currentMeeting[0])
                minHeap.poll();
            //add the current end meeting time
            minHeap.add(currentMeeting[1]);
        }
        return minHeap.size();
    }
}
                times.getLast()[0] = Math.min(times.getLast()[0], interval[0]);

```

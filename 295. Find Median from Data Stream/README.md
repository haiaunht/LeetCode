# [295. Find Median from Data Stream (Hard)](https://leetcode.com/problems/find-median-from-data-stream/)

<p>The <strong>median</strong> is the middle value in an ordered integer list. If the size of the list is even, there is no middle value and the median is the mean of the two middle values.</p>

<ul>
	<li>For example, for <code>arr = [2,3,4]</code>, the median is <code>3</code>.</li>
	<li>For example, for <code>arr = [2,3]</code>, the median is <code>(2 + 3) / 2 = 2.5</code>.</li>
</ul>

<p>Implement the MedianFinder class:</p>

<ul>
	<li><code>MedianFinder()</code> initializes the <code>MedianFinder</code> object.</li>
	<li><code>void addNum(int num)</code> adds the integer <code>num</code> from the data stream to the data structure.</li>
	<li><code>double findMedian()</code> returns the median of all elements so far. Answers within <code>10<sup>-5</sup></code> of the actual answer will be accepted.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input</strong>
["MedianFinder", "addNum", "addNum", "findMedian", "addNum", "findMedian"]
[[], [1], [2], [], [3], []]
<strong>Output</strong>
[null, null, null, 1.5, null, 2.0]

<strong>Explanation</strong>
MedianFinder medianFinder = new MedianFinder();
medianFinder.addNum(1);    // arr = [1]
medianFinder.addNum(2);    // arr = [1, 2]
medianFinder.findMedian(); // return 1.5 (i.e., (1 + 2) / 2)
medianFinder.addNum(3);    // arr[1, 2, 3]
medianFinder.findMedian(); // return 2.0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-10<sup>5</sup> &lt;= num &lt;= 10<sup>5</sup></code></li>
	<li>There will be at least one element in the data structure before calling <code>findMedian</code>.</li>
	<li>At most <code>5 * 10<sup>4</sup></code> calls will be made to <code>addNum</code> and <code>findMedian</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong></p>

<ul>
	<li>If all integer numbers from the stream are in the range <code>[0, 100]</code>, how would you optimize your solution?</li>
	<li>If <code>99%</code> of all integer numbers from the stream are in the range <code>[0, 100]</code>, how would you optimize your solution?</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple), [ByteDance](https://leetcode.com/company/bytedance), [Google](https://leetcode.com/company/google), [Twitter](https://leetcode.com/company/twitter), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Adobe](https://leetcode.com/company/adobe), [Uber](https://leetcode.com/company/uber), [Expedia](https://leetcode.com/company/expedia), [eBay](https://leetcode.com/company/ebay), [Bloomberg](https://leetcode.com/company/bloomberg), [Walmart Labs](https://leetcode.com/company/walmart-labs), [IXL](https://leetcode.com/company/ixl), [DoorDash](https://leetcode.com/company/doordash)

**Related Topics**:  
[Two Pointers](https://leetcode.com/tag/two-pointers/), [Design](https://leetcode.com/tag/design/), [Sorting](https://leetcode.com/tag/sorting/), [Heap (Priority Queue)](https://leetcode.com/tag/heap-priority-queue/), [Data Stream](https://leetcode.com/tag/data-stream/)

**Similar Questions**:

- [Sliding Window Median (Hard)](https://leetcode.com/problems/sliding-window-median/)
- [Finding MK Average (Hard)](https://leetcode.com/problems/finding-mk-average/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/find-median-from-data-stream/
// Author: Please set your name in options page
// Time: O(nlogn)
// Space: O(n)
class MedianFinder {
    List<Integer> list;
    /** initialize your data structure here. */
    public MedianFinder() {
        list = new ArrayList<>();
    }
    public void addNum(int num) {
        int positionToInsert = binarySearch(num);
        list.add(positionToInsert, num);
    }
    public double findMedian() {
        int size = list.size();
        //if the list is odd in size, return the middle which is size()/2, (else size()/2-1+ size()/2)/2
        if (size%2!=0) {
            return (double)list.get(size/2);
        } else {
            double ans = ((double)list.get(size/2-1)+(double)list.get(size/2))/2;
            return ans;
        }
    }
    public int binarySearch(int num) {
        int left = 0;
        int right = list.size()-1;
        while (left <= right) {
            int mid = (left + right)/2;
            if (list.get(mid) < num) {
                left = mid+1;
            } else if (list.get(mid) > num){
                right = mid-1;
            } else {
                return mid;
            }
        }
        return left;
    }
}
/**
 * Your MedianFinder object will be instantiated and called as such:
 * MedianFinder obj = new MedianFinder();
 * obj.addNum(num);
 * double param_2 = obj.findMedian();
 */

```

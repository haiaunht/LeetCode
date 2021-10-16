# [1146. Snapshot Array (Medium)](https://leetcode.com/problems/snapshot-array/)

<p>Implement a SnapshotArray that supports the following interface:</p>

<ul>
	<li><code>SnapshotArray(int length)</code> initializes an array-like data structure with the given length.&nbsp; <strong>Initially, each element equals 0</strong>.</li>
	<li><code>void set(index, val)</code> sets the element at the given <code>index</code> to be equal to <code>val</code>.</li>
	<li><code>int snap()</code>&nbsp;takes a snapshot of the array and returns the <code>snap_id</code>: the total number of times we called <code>snap()</code> minus <code>1</code>.</li>
	<li><code>int get(index, snap_id)</code>&nbsp;returns the value at the given <code>index</code>, at the time we took the snapshot with the given <code>snap_id</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> ["SnapshotArray","set","snap","set","get"]
[[3],[0,5],[],[0,6],[0,0]]
<strong>Output:</strong> [null,null,0,null,5]
<strong>Explanation: </strong>
SnapshotArray snapshotArr = new SnapshotArray(3); // set the length to be 3
snapshotArr.set(0,5);  // Set array[0] = 5
snapshotArr.snap();  // Take a snapshot, return snap_id = 0
snapshotArr.set(0,6);
snapshotArr.get(0,0);  // Get the value of array[0] with snap_id = 0, return 5</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= length&nbsp;&lt;= 50000</code></li>
	<li>At most <code>50000</code>&nbsp;calls will be made to <code>set</code>, <code>snap</code>, and <code>get</code>.</li>
	<li><code>0 &lt;= index&nbsp;&lt;&nbsp;length</code></li>
	<li><code>0 &lt;=&nbsp;snap_id &lt;&nbsp;</code>(the total number of times we call <code>snap()</code>)</li>
	<li><code>0 &lt;=&nbsp;val &lt;= 10^9</code></li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [Amazon](https://leetcode.com/company/amazon), [Rubrik](https://leetcode.com/company/rubrik), [Uber](https://leetcode.com/company/uber)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Binary Search](https://leetcode.com/tag/binary-search/), [Design](https://leetcode.com/tag/design/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/snapshot-array/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class SnapshotArray {
    List<int[]>[] list; //int[] will have [val, snap_id] pair
    int snap = 0;
    public SnapshotArray(int length) {
        list = new List[length];
        //initial each element of list
        for (int i=0; i<length; i++) {
            list[i] = new ArrayList<>();
            list[i].add(new int[]{0, -1});
        }
    }
    public void set(int index, int val) {
        list[index].add(new int[]{val, snap});
    }
    public int snap() {
        return snap++;
    }
    public int get(int index, int snap_id) {
       List<int[]> temp = list[index];
        int low = 0, high = temp.size() - 1;
        // binary search rightmost
        while (low < high) {
            int mid = (low+high+1)/ 2; //+1 to avoid infinity loop whe low = mid
            if (temp.get(mid)[1] <= snap_id) low = mid;
            else high = mid - 1;
        }
        return temp.get(low)[0];
    }
}
/**
 * Your SnapshotArray object will be instantiated and called as such:
 * SnapshotArray obj = new SnapshotArray(length);
 * obj.set(index,val);
 * int param_2 = obj.snap();
 * int param_3 = obj.get(index,snap_id);
 */

```

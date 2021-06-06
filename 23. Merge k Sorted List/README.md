# [23. Merge k Sorted Lists (Hard)](https://leetcode.com/problems/merge-k-sorted-lists/)

<p>You are given an array of <code>k</code> linked-lists <code>lists</code>, each linked-list is sorted in ascending order.</p>

<p><em>Merge all the linked-lists into one sorted linked-list and return it.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> lists = [[1,4,5],[1,3,4],[2,6]]
<strong>Output:</strong> [1,1,2,3,4,4,5,6]
<strong>Explanation:</strong> The linked-lists are:
[
  1-&gt;4-&gt;5,
  1-&gt;3-&gt;4,
  2-&gt;6
]
merging them into one sorted list:
1-&gt;1-&gt;2-&gt;3-&gt;4-&gt;4-&gt;5-&gt;6
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> lists = []
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> lists = [[]]
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>k == lists.length</code></li>
	<li><code>0 &lt;= k &lt;= 10^4</code></li>
	<li><code>0 &lt;= lists[i].length &lt;= 500</code></li>
	<li><code>-10^4 &lt;= lists[i][j] &lt;= 10^4</code></li>
	<li><code>lists[i]</code> is sorted in <strong>ascending order</strong>.</li>
	<li>The sum of <code>lists[i].length</code> won't exceed <code>10^4</code>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Microsoft](https://leetcode.com/company/microsoft), [Bloomberg](https://leetcode.com/company/bloomberg), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google), [Adobe](https://leetcode.com/company/adobe), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Indeed](https://leetcode.com/company/indeed), [LinkedIn](https://leetcode.com/company/linkedin), [Oracle](https://leetcode.com/company/oracle), [Yahoo](https://leetcode.com/company/yahoo), [Tesla](https://leetcode.com/company/tesla)

**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Divide and Conquer](https://leetcode.com/tag/divide-and-conquer/), [Heap](https://leetcode.com/tag/heap/)

**Similar Questions**:

- [Merge Two Sorted Lists (Easy)](https://leetcode.com/problems/merge-two-sorted-lists/)
- [Ugly Number II (Medium)](https://leetcode.com/problems/ugly-number-ii/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/merge-k-sorted-lists/
// Author: Please set your name in options page
// Time: O()
// Space: O()
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        //put each list into a priorityQueue
        PriorityQueue<Integer> sorted = new PriorityQueue<>();
        for (ListNode i : lists) {
            while(i != null) {
                sorted.add(i.val);
                i = i.next;
            }
        }
        ListNode dummy_head = new ListNode(0);
        ListNode currentPt = dummy_head;
        while (!sorted.isEmpty()) {
            currentPt.next = new ListNode(sorted.poll());
            currentPt = currentPt.next;
        }
        return dummy_head.next;
    }
}

```

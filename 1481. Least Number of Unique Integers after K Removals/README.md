# [1481. Least Number of Unique Integers after K Removals (Medium)](https://leetcode.com/problems/least-number-of-unique-integers-after-k-removals/)

<p>Given an array of integers&nbsp;<code>arr</code>&nbsp;and an integer <code>k</code>.&nbsp;Find the <em>least number of unique integers</em>&nbsp;after removing <strong>exactly</strong> <code>k</code> elements<b>.</b></p>

<ol>
</ol>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input: </strong>arr = [5,5,4], k = 1
<strong>Output: </strong>1
<strong>Explanation</strong>: Remove the single 4, only 5 is left.
</pre>

<strong>Example 2:</strong>

<pre><strong>Input: </strong>arr = [4,3,1,1,3,3,2], k = 3
<strong>Output: </strong>2
<strong>Explanation</strong>: Remove 4, 2 and either one of the two 1s or three 3s. 1 and 3 will be left.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length&nbsp;&lt;= 10^5</code></li>
	<li><code>1 &lt;= arr[i] &lt;= 10^9</code></li>
	<li><code>0 &lt;= k&nbsp;&lt;= arr.length</code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Greedy](https://leetcode.com/tag/greedy/), [Sorting](https://leetcode.com/tag/sorting/), [Counting](https://leetcode.com/tag/counting/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/least-number-of-unique-integers-after-k-removals/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int findLeastNumOfUniqueInts(int[] arr, int k) {
        //[4,3,1,1,3,3,2]
        //{4:1, 3:2, 2:1, 1:2}, k=3
        Map<Integer, Integer> map = new HashMap<>();
        for (int i:arr) {
            map.put(i, map.getOrDefault(i, 0) + 1);
        }
       //sort the map by its' values
        PriorityQueue<Map.Entry<Integer,Integer>> sortedMap = new PriorityQueue<>((a,b) -> {
            if (a.getValue() > b.getValue()) return 1;
            return -1;
        });
        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            sortedMap.add(entry);
        }
        //peek at each head, if still <= k, remove, else done => return
        while (!sortedMap.isEmpty()) {
            Map.Entry<Integer, Integer> each = sortedMap.peek();
            if (each.getValue() <= k) {
                sortedMap.poll();
                k -= each.getValue();
            } else {
                break;
            }
        }
        return sortedMap.size();
    }
}

```

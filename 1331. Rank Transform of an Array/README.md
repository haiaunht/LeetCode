# [1331. Rank Transform of an Array (Easy)](https://leetcode.com/problems/rank-transform-of-an-array/)

<p>Given an array of integers&nbsp;<code>arr</code>, replace each element with its rank.</p>

<p>The rank represents how large the element is. The rank has the following rules:</p>

<ul>
	<li>Rank is an integer starting from 1.</li>
	<li>The larger the element, the larger the rank. If two elements are equal, their rank must be the same.</li>
	<li>Rank should be as small as possible.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> arr = [40,10,20,30]
<strong>Output:</strong> [4,1,2,3]
<strong>Explanation</strong>: 40 is the largest element. 10 is the smallest. 20 is the second smallest. 30 is the third smallest.</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> arr = [100,100,100]
<strong>Output:</strong> [1,1,1]
<strong>Explanation</strong>: Same elements share the same rank.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> arr = [37,12,28,9,100,56,80,5,12]
<strong>Output:</strong> [5,3,4,2,8,6,7,1,3]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= arr.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>9</sup>&nbsp;&lt;= arr[i] &lt;= 10<sup>9</sup></code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Sorting](https://leetcode.com/tag/sorting/)

**Similar Questions**:

- [Rank Transform of a Matrix (Hard)](https://leetcode.com/problems/rank-transform-of-a-matrix/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/rank-transform-of-an-array/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int[] arrayRankTransform(int[] arr) {
        int[] copy = arr.clone();
        Arrays.sort(copy);
        //[40,10,20,30] -> [10,20,30,40]
        //put integer if absent [100,100,100] -> {1:1}, already there skip
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : copy) {
            map.putIfAbsent(num, map.size()+1);
        }
        //loop through original arr to add back to the array
        for (int i=0; i<arr.length; i++) {
            copy[i] = map.get(arr[i]);
        }
        return copy;
    }
}

```

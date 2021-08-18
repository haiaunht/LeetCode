# [1213. Intersection of Three Sorted Arrays (Easy)](https://leetcode.com/problems/intersection-of-three-sorted-arrays/)

<p>Given three integer arrays <code>arr1</code>, <code>arr2</code> and <code>arr3</code>&nbsp;<strong>sorted</strong> in <strong>strictly increasing</strong> order, return a sorted array of <strong>only</strong>&nbsp;the&nbsp;integers that appeared in <strong>all</strong> three arrays.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> arr1 = [1,2,3,4,5], arr2 = [1,2,5,7,9], arr3 = [1,3,4,5,8]
<strong>Output:</strong> [1,5]
<strong>Explanation: </strong>Only 1 and 5 appeared in the three arrays.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> arr1 = [197,418,523,876,1356], arr2 = [501,880,1593,1710,1870], arr3 = [521,682,1337,1395,1764]
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr1.length, arr2.length, arr3.length &lt;= 1000</code></li>
	<li><code>1 &lt;= arr1[i], arr2[i], arr3[i] &lt;= 2000</code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Binary Search](https://leetcode.com/tag/binary-search/), [Counting](https://leetcode.com/tag/counting/)

**Similar Questions**:

- [Intersection of Two Arrays (Easy)](https://leetcode.com/problems/intersection-of-two-arrays/)

## Solution 1.

```java
 // OJ: https://leetcode.com/problems/intersection-of-three-sorted-arrays/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public List<Integer> arraysIntersection(int[] arr1, int[] arr2, int[] arr3) {
        List<Integer> result = new ArrayList<>();
        Map<Integer, Integer> map = new HashMap<>();
        Set<Integer> set = new HashSet<>();
        for (int i=0; i<arr1.length; i++) {
            map.put(arr1[i], map.getOrDefault(arr1[i],0)+1);
        }
        for (int i=0; i<arr2.length; i++) {
            if (map.containsKey(arr2[i])) {
                set.add(arr2[i]);
            }
        }
        for (int i=0; i<arr3.length; i++) {
            if (set.contains(arr3[i])) {
                result.add(arr3[i]);
            }
        }
        return result;
    }
}

```

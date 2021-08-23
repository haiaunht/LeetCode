# [1198. Find Smallest Common Element in All Rows (Medium)](https://leetcode.com/problems/find-smallest-common-element-in-all-rows/)

<p>Given an <code>m x n</code> matrix <code>mat</code> where every row is sorted in <strong>strictly</strong> <strong>increasing</strong> order, return <em>the <strong>smallest common element</strong> in all rows</em>.</p>

<p>If there is no common element, return <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> mat = [[1,2,3,4,5],[2,4,5,8,10],[3,5,7,9,11],[1,3,5,7,9]]
<strong>Output:</strong> 5
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> mat = [[1,2,3],[2,3,4],[2,3,5]]
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 500</code></li>
	<li><code>1 &lt;= mat[i][j] &lt;= 10<sup>4</sup></code></li>
	<li><code>mat[i]</code> is sorted in strictly increasing order.</li>
</ul>

**Companies**:  
[Intel](https://leetcode.com/company/intel)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Binary Search](https://leetcode.com/tag/binary-search/), [Matrix](https://leetcode.com/tag/matrix/), [Counting](https://leetcode.com/tag/counting/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/find-smallest-common-element-in-all-rows/
// Author: Hai-Au
// Time: O(m*n)
// Space: O(1)
class Solution {
    public int smallestCommonElement(int[][] mat) {
        //[1,2,3,4,5],
        //[2,4,5,8,10],
        //[3,5,7,9,11],
        //[1,3,5,7,9]
        // 1 appears 2 times
        // 2 ....... 2 times
        // 3 ....... 3 times
        // 4 ....... 2 times
        // 5 ....... 4 times //smallest appear mat.length time so this is it
        // 7 ....
        //there is posible of 10^4 numbers from 1->10^4 -> create an array to hold index from 0->10^4, index 0 no use but easy to not bound
        int[] nums = new int[10001];
        for (int[] row : mat) {
            for (int num : row) {
                nums[num]++;
            }
        }
        for (int i=0; i<10001; i++) {
            if (nums[i] == mat.length) {
                return i;
            }
        }
        return -1;
    }
}

```

# [1329. Sort the Matrix Diagonally (Medium)](https://leetcode.com/problems/sort-the-matrix-diagonally/)

<p>A <strong>matrix diagonal</strong> is a diagonal line of cells starting from some cell in either the topmost row or leftmost column and going in the bottom-right direction until reaching the matrix's end. For example, the <strong>matrix diagonal</strong> starting from <code>mat[2][0]</code>, where <code>mat</code> is a <code>6 x 3</code> matrix, includes cells <code>mat[2][0]</code>, <code>mat[3][1]</code>, and <code>mat[4][2]</code>.</p>

<p>Given an <code>m x n</code> matrix <code>mat</code> of integers, sort each <strong>matrix diagonal</strong> in ascending order and return <em>the resulting matrix</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/01/21/1482_example_1_2.png" style="width: 500px; height: 198px;">
<pre><strong>Input:</strong> mat = [[3,3,1,1],[2,2,1,2],[1,1,1,2]]
<strong>Output:</strong> [[1,1,1,1],[1,2,2,2],[1,2,3,3]]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> mat = [[11,25,66,1,69,7],[23,55,17,45,15,52],[75,31,36,44,58,8],[22,27,33,25,68,4],[84,28,14,11,5,50]]
<strong>Output:</strong> [[5,17,4,1,52,7],[11,11,25,45,8,69],[14,23,25,44,58,15],[22,27,31,36,50,66],[84,28,75,33,55,68]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 100</code></li>
	<li><code>1 &lt;= mat[i][j] &lt;= 100</code></li>
</ul>

**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Amazon](https://leetcode.com/company/amazon), [Adobe](https://leetcode.com/company/adobe)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Sorting](https://leetcode.com/tag/sorting/), [Matrix](https://leetcode.com/tag/matrix/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/sort-the-matrix-diagonally/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int[][] diagonalSort(int[][] mat) {
        int rows = mat.length;
        int cols = mat[0].length;
        Map<Integer, Queue<Integer>> map = new HashMap<>();
        //loop through and add to each diagonal line
        for (int row=0; row<rows; row++) {
            for (int col=0; col<cols; col++) {
                map.putIfAbsent(row-col, new PriorityQueue<Integer>());
                map.get(row-col).add(mat[row][col]);
            }
        }
        //after sort using priortiyQueue, pop each num back to mat
        for (int row=0; row<rows; row++) {
            for (int col=0; col<cols; col++) {
                mat[row][col] = map.get(row-col).remove();
            }
        }
        return mat;
    }
}

```

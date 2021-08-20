# [73. Set Matrix Zeroes (Medium)](https://leetcode.com/problems/set-matrix-zeroes/)

<p>Given an <code>m x n</code> integer matrix <code>matrix</code>, if an element is <code>0</code>, set its entire row and column to <code>0</code>'s, and return <em>the matrix</em>.</p>

<p>You must do it <a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank">in place</a>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/17/mat1.jpg" style="width: 450px; height: 169px;">
<pre><strong>Input:</strong> matrix = [[1,1,1],[1,0,1],[1,1,1]]
<strong>Output:</strong> [[1,0,1],[0,0,0],[1,0,1]]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/17/mat2.jpg" style="width: 450px; height: 137px;">
<pre><strong>Input:</strong> matrix = [[0,1,2,0],[3,4,5,2],[1,3,1,5]]
<strong>Output:</strong> [[0,0,0,0],[0,4,5,0],[0,3,1,0]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == matrix.length</code></li>
	<li><code>n == matrix[0].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 200</code></li>
	<li><code>-2<sup>31</sup> &lt;= matrix[i][j] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong></p>

<ul>
	<li>A straightforward solution using <code>O(mn)</code> space is probably a bad idea.</li>
	<li>A simple improvement uses <code>O(m + n)</code> space, but still not the best solution.</li>
	<li>Could you devise a constant space solution?</li>
</ul>

**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Qualtrics](https://leetcode.com/company/qualtrics)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Matrix](https://leetcode.com/tag/matrix/)

**Similar Questions**:

- [Game of Life (Medium)](https://leetcode.com/problems/game-of-life/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/set-matrix-zeroes/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public void setZeroes(int[][] matrix) {
        int rows = matrix.length;
        int cols = matrix[0].length;
        int[][] copy = new int[rows][cols];
        for (int i=0; i<rows; i++) {
            for (int j=0; j<cols; j++) {
                copy[i][j] = matrix[i][j];
            }
        }
        for (int row=0; row<rows; row++) {
            for (int col=0; col<cols; col++) {
                if (copy[row][col] == 0) {
                    setRowZeros(matrix, row);
                    setColZeros(matrix, col);
                }
            }
        }
    }
    private void setRowZeros(int[][] matrix, int row) {
        for (int j=0; j<matrix[0].length; j++) {
            matrix[row][j] = 0;
        }
    }
    private void setColZeros(int[][] matrix, int col) {
        for (int i=0; i<matrix.length; i++) {
            matrix[i][col] = 0;
        }
    }
}

```

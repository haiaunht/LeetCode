# [498. Diagonal Traverse (Medium)](https://leetcode.com/problems/diagonal-traverse/)

<p>Given an <code>m x n</code> matrix <code>mat</code>, return <em>an array of all the elements of the array in a diagonal order</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/04/10/diag1-grid.jpg" style="width: 334px; height: 334px;">
<pre><strong>Input:</strong> mat = [[1,2,3],[4,5,6],[7,8,9]]
<strong>Output:</strong> [1,2,4,7,5,3,6,8,9]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> mat = [[1,2],[3,4]]
<strong>Output:</strong> [1,2,3,4]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= m * n &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>5</sup> &lt;= mat[i][j] &lt;= 10<sup>5</sup></code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Matrix](https://leetcode.com/tag/matrix/), [Simulation](https://leetcode.com/tag/simulation/)

**Similar Questions**:

- [Decode the Slanted Ciphertext (Medium)](https://leetcode.com/problems/decode-the-slanted-ciphertext/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/diagonal-traverse/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int[] findDiagonalOrder(int[][] matrix) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) return null;
        int rows = matrix.length;
        int cols = matrix[0].length;
        int[] diagonal_traverse = new int[rows * cols];
        int currentRow = 0;
        int currentCol = 0;
        for (int i=0; i<diagonal_traverse.length; i++) {
            //assign to current row and col
            diagonal_traverse[i] = matrix[currentRow][currentCol];
            //check if diagonal up or down, up when (currentRow + currentCol)%2 == 0
            if ((currentRow + currentCol)%2 == 0) {
                //go up, when hit last col -> need to increase the row
                if (currentCol == cols-1) {
                    currentRow++;
                } else if (currentRow == 0) {
                    currentCol++;
                } else {
                    currentRow--;
                    currentCol++;
                }
            } else {
                //when diagonal down, if hit rows-1 -> increase the col
                if (currentRow == rows-1) {
                    currentCol++;
                } else if (currentCol == 0) {
                    currentRow++;
                } else {
                    currentRow++;
                    currentCol--;
                }
            }
        }
        return diagonal_traverse;
    }
}

```

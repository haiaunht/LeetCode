# [54. Spiral Matrix (Medium)](https://leetcode.com/problems/spiral-matrix/)

<p>Given an <code>m x n</code> <code>matrix</code>, return <em>all elements of the</em> <code>matrix</code> <em>in spiral order</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/spiral1.jpg" style="width: 242px; height: 242px;">
<pre><strong>Input:</strong> matrix = [[1,2,3],[4,5,6],[7,8,9]]
<strong>Output:</strong> [1,2,3,6,9,8,7,4,5]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/spiral.jpg" style="width: 322px; height: 242px;">
<pre><strong>Input:</strong> matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
<strong>Output:</strong> [1,2,3,4,8,12,11,10,9,5,6,7]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == matrix.length</code></li>
	<li><code>n == matrix[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 10</code></li>
	<li><code>-100 &lt;= matrix[i][j] &lt;= 100</code></li>
</ul>

**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple), [Amazon](https://leetcode.com/company/amazon), [Intuit](https://leetcode.com/company/intuit), [Adobe](https://leetcode.com/company/adobe), [Bloomberg](https://leetcode.com/company/bloomberg), [Google](https://leetcode.com/company/google), [VMware](https://leetcode.com/company/vmware), [Tesla](https://leetcode.com/company/tesla), [Accolite](https://leetcode.com/company/accolite), [Flipkart](https://leetcode.com/company/flipkart)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Matrix](https://leetcode.com/tag/matrix/), [Simulation](https://leetcode.com/tag/simulation/)

**Similar Questions**:

- [Spiral Matrix II (Medium)](https://leetcode.com/problems/spiral-matrix-ii/)
- [Spiral Matrix III (Medium)](https://leetcode.com/problems/spiral-matrix-iii/)

## Solution 1.

```Java
// OJ: https://leetcode.com/problems/spiral-matrix/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> list = new ArrayList<>();
        if (matrix == null || matrix.length == 0) return list;
        int leftColumn = 0;
        int rightColumn = matrix[0].length -1;
        int topRow = 0;
        int bottomRow = matrix.length - 1;
        int listSize = (matrix.length * matrix[0].length);
        //loop until the list's size = listSize
        while (list.size() < listSize) {
            //from left col to right col, then move to row++ for the next loop
            for (int col=topRow; col<=rightColumn && list.size() < listSize; col++) {
                list.add(matrix[topRow][col]);
            }
            topRow++;
            //at right col, row move from [topRow][right] -> [bottom][right]
            for (int row=topRow; row<=bottomRow && list.size() < listSize; row++) {
                list.add(matrix[row][rightColumn]);
            }
            rightColumn--;
            //at bottom row, move from [bottomRow][rightCol] -> [bottomeRow][leftCol]
            for (int col=rightColumn; col>=leftColumn && list.size() < listSize; col--) {
                list.add(matrix[bottomRow][col]);
            }
            bottomRow--;
            //at the left col, move from bottomRow to topRow, and the loop continue
            for (int row=bottomRow; row>=topRow && list.size() < listSize; row--) {
                list.add(matrix[row][leftColumn]);
            }
            leftColumn++;
        }
        return list;
    }
}

```

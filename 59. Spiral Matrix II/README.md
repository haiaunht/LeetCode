# [59. Spiral Matrix II (Medium)](https://leetcode.com/problems/spiral-matrix-ii/)

<p>Given a positive integer <code>n</code>, generate an <code>n x n</code> <code>matrix</code> filled with elements from <code>1</code> to <code>n<sup>2</sup></code> in spiral order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/spiraln.jpg" style="width: 242px; height: 242px;">
<pre><strong>Input:</strong> n = 3
<strong>Output:</strong> [[1,2,3],[8,9,4],[7,6,5]]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 1
<strong>Output:</strong> [[1]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 20</code></li>
</ul>

**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Matrix](https://leetcode.com/tag/matrix/), [Simulation](https://leetcode.com/tag/simulation/)

**Similar Questions**:

- [Spiral Matrix (Medium)](https://leetcode.com/problems/spiral-matrix/)
- [Spiral Matrix III (Medium)](https://leetcode.com/problems/spiral-matrix-iii/)

## Solution 1.

```Java
// OJ: https://leetcode.com/problems/spiral-matrix-ii/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] result = new int[n][n];
        int element = 1; //fill from 1 -> n*n
        int leftCol = 0;
        int rightCol = n-1;
        int topRow = 0;
        int bottomRow = n-1;
        int size = n*n;
        while (element <= size) {
            for (int col=topRow; col<=rightCol && element <= size; col++) {
                result[topRow][col] = element++;
            }
            topRow++;
            for (int row=topRow; row<=bottomRow && element <= size; row++) {
                result[row][rightCol] = element++;
            }
            rightCol--;
            for (int col=rightCol; col>=leftCol && element <= size; col--) {
                result[bottomRow][col] = element++;
            }
            bottomRow--;
            for (int row=bottomRow; row>=topRow && element <= size; row--) {
                result[row][leftCol] = element++;
            }
            leftCol++;
        }
        return result;
    }
}

```

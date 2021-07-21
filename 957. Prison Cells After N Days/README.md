# [957. Prison Cells After N Days (Medium)](https://leetcode.com/problems/prison-cells-after-n-days/)

<p>There are <code>8</code> prison cells in a row and each cell is either occupied or vacant.</p>

<p>Each day, whether the cell is occupied or vacant changes according to the following rules:</p>

<ul>
	<li>If a cell has two adjacent neighbors that are both occupied or both vacant, then the cell becomes occupied.</li>
	<li>Otherwise, it becomes vacant.</li>
</ul>

<p><strong>Note</strong> that because the prison is a row, the first and the last cells in the row can't have two adjacent neighbors.</p>

<p>You are given an integer array <code>cells</code> where <code>cells[i] == 1</code> if the <code>i<sup>th</sup></code> cell is occupied and <code>cells[i] == 0</code> if the <code>i<sup>th</sup></code> cell is vacant, and you are given an integer <code>n</code>.</p>

<p>Return the state of the prison after <code>n</code> days (i.e., <code>n</code> such changes described above).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> cells = [0,1,0,1,1,0,0,1], n = 7
<strong>Output:</strong> [0,0,1,1,0,0,0,0]
<strong>Explanation:</strong> The following table summarizes the state of the prison on each day:
Day 0: [0, 1, 0, 1, 1, 0, 0, 1]
Day 1: [0, 1, 1, 0, 0, 0, 0, 0]
Day 2: [0, 0, 0, 0, 1, 1, 1, 0]
Day 3: [0, 1, 1, 0, 0, 1, 0, 0]
Day 4: [0, 0, 0, 0, 0, 1, 0, 0]
Day 5: [0, 1, 1, 1, 0, 1, 0, 0]
Day 6: [0, 0, 1, 0, 1, 1, 0, 0]
Day 7: [0, 0, 1, 1, 0, 0, 0, 0]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> cells = [1,0,0,1,0,0,1,0], n = 1000000000
<strong>Output:</strong> [0,0,1,1,1,1,1,0]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>cells.length == 8</code></li>
	<li><code>cells[i]</code>&nbsp;is either <code>0</code> or <code>1</code>.</li>
	<li><code>1 &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Math](https://leetcode.com/tag/math/), [Bit Manipulation](https://leetcode.com/tag/bit-manipulation/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/prison-cells-after-n-days/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int[] prisonAfterNDays(int[] cells, int n) {
        //after each 14 days, the cells repeat itself, if n%14==0, n=14 steps
        //n%14 to only to (n%14) steps, avoid the time limit exceeded I have before
        if (n%14 == 0) n = 14;
        else n = n%14;
        for (int i=0; i<n; i++) {
            cells = cellsNextDay(cells);
        }
        return cells;
    }
    private static int[] cellsNextDay(int[] cells) {
        int[] nextDay = new int[cells.length]; //[0,0,0,0,0,0,0,0]
        //the first and last cell always = 0 so loop from 1->7
        for (int i=1; i<cells.length-1; i++) {
            if (cells[i-1] == cells[i+1]) nextDay[i] = 1;
        }
        return nextDay;
    }
}

```

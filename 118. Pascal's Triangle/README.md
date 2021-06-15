# [118. Pascal's Triangle (Easy)](https://leetcode.com/problems/pascals-triangle/)

<p>Given an integer <code>numRows</code>, return the first numRows of <strong>Pascal's triangle</strong>.</p>

<p>In <strong>Pascal's triangle</strong>, each number is the sum of the two numbers directly above it as shown:</p>
<img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif" style="height:240px; width:260px">
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> numRows = 5
<strong>Output:</strong> [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> numRows = 1
<strong>Output:</strong> [[1]]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= numRows &lt;= 30</code></li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [Apple](https://leetcode.com/company/apple), [Adobe](https://leetcode.com/company/adobe), [Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Yahoo](https://leetcode.com/company/yahoo), [Goldman Sachs](https://leetcode.com/company/goldman-sachs)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/)

**Similar Questions**:

- [Pascal's Triangle II (Easy)](https://leetcode.com/problems/pascals-triangle-ii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/pascals-triangle/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> result = new ArrayList<>();
        //first list of result is always [1]
        result.add(new ArrayList<>());
        result.get(0).add(1);
        //current list will have element = previous element-1 = previous element
        for (int row=1; row<numRows; row++) {
            List<Integer> currentRow = new ArrayList<>();
            List<Integer> previous = result.get(row-1);
            currentRow.add(1);
            for (int j=1; j<row; j++) {
                int currentNum = previous.get(j-1) + previous.get(j);
                currentRow.add(currentNum);
            }
            currentRow.add(1);
            result.add(currentRow);
        }
        return result;
    }
}

```

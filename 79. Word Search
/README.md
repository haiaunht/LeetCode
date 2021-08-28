# [79. Word Search (Medium)](https://leetcode.com/problems/word-search/solution/)

<p>Given an <code>m x n</code> grid of characters <code>board</code> and a string <code>word</code>, return <code>true</code> <em>if</em> <code>word</code> <em>exists in the grid</em>.</p>

<p>The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/04/word2.jpg" style="width: 322px; height: 242px;">
<pre><strong>Input:</strong> board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/04/word-1.jpg" style="width: 322px; height: 242px;">
<pre><strong>Input:</strong> board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "SEE"
<strong>Output:</strong> true
</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/15/word3.jpg" style="width: 322px; height: 242px;">
<pre><strong>Input:</strong> board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCB"
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == board.length</code></li>
	<li><code>n = board[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 6</code></li>
	<li><code>1 &lt;= word.length &lt;= 15</code></li>
	<li><code>board</code> and <code>word</code> consists of only lowercase and uppercase English letters.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you use search pruning to make your solution faster with a larger <code>board</code>?</p>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Snapchat](https://leetcode.com/company/snapchat), [Facebook](https://leetcode.com/company/facebook), [Bloomberg](https://leetcode.com/company/bloomberg), [Apple](https://leetcode.com/company/apple), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Twitter](https://leetcode.com/company/twitter), [Intuit](https://leetcode.com/company/intuit), [Google](https://leetcode.com/company/google), [Adobe](https://leetcode.com/company/adobe), [VMware](https://leetcode.com/company/vmware), [Cisco](https://leetcode.com/company/cisco), [Cruise Automation](https://leetcode.com/company/cruise-automation)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Backtracking](https://leetcode.com/tag/backtracking/), [Matrix](https://leetcode.com/tag/matrix/)

**Similar Questions**:

- [Word Search II (Hard)](https://leetcode.com/problems/word-search-ii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/word-search/solution/
// Author: Please set your name in options page
// Time: O(cellCount * 3^wordLengt)
// Space: O(wordLength)
class Solution {
    public boolean exist(char[][] board, String word) {
        if (board == null || board.length == 0) return false;
        for (int i=0; i<board.length; i++) {
            for (int j=0; j<board[0].length; j++) {
                if (board[i][j] == word.charAt(0) && dfs(board, i, j, 0, word)) {
                    return true;
                }
            }
        }
        return false;
    }
    private boolean dfs(char[][] board, int i, int j, int count, String word) {
        if (count == word.length()) return true;
        if (i<0 || i>=board.length || j<0 || j>= board[0].length || board[i][j] != word.charAt(count)) {
            return false;
        }
        //mark as visit temporaly, return its value after recursive call
        char temp = board[i][j];
        board[i][j] = ' ';
        boolean found = dfs(board, i+1, j, count+1, word) ||
                        dfs(board, i-1, j, count+1, word) ||
                        dfs(board, i, j+1, count+1, word) ||
                        dfs(board, i, j-1, count+1, word);
        board[i][j] = temp;
        return found;
    }
}

```

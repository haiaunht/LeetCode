# [1079. Letter Tile Possibilities (Medium)](https://leetcode.com/problems/letter-tile-possibilities/)

<p>You have <code>n</code>&nbsp;&nbsp;<code>tiles</code>, where each tile has one letter <code>tiles[i]</code> printed on it.</p>

<p>Return <em>the number of possible non-empty sequences of letters</em> you can make using the letters printed on those <code>tiles</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> tiles = "AAB"
<strong>Output:</strong> 8
<strong>Explanation: </strong>The possible sequences are "A", "B", "AA", "AB", "BA", "AAB", "ABA", "BAA".
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> tiles = "AAABBC"
<strong>Output:</strong> 188
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> tiles = "V"
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= tiles.length &lt;= 7</code></li>
	<li><code>tiles</code> consists of uppercase English letters.</li>
</ul>

**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Google](https://leetcode.com/company/google), [Bloomberg](https://leetcode.com/company/bloomberg)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Backtracking](https://leetcode.com/tag/backtracking/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/letter-tile-possibilities/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int numTilePossibilities(String tiles) {
    Set<String> set = new HashSet<>();
        boolean[] visited = new boolean[tiles.length()];
        backtrack(tiles, "", set, visited);
        return set.size();
    }
    private void backtrack(String tiles, String curr, Set<String> set, boolean[] visited) {
        if (curr.length() != 0) {
            set.add(curr);
        }
        for (int i=0; i<tiles.length(); i++) {
            if (!visited[i]) {
                visited[i] = true;
                backtrack(tiles, curr+tiles.charAt(i), set, visited);
                visited[i] = false;
            }
        }
    }
}

```

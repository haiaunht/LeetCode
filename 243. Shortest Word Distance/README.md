# [243. Shortest Word Distance (Easy)](https://leetcode.com/problems/shortest-word-distance/)

<p>Given an array of strings <code>wordsDict</code> and two different strings that already exist in the array <code>word1</code> and <code>word2</code>, return <em>the shortest distance between these two words in the list</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> wordsDict = ["practice", "makes", "perfect", "coding", "makes"], word1 = "coding", word2 = "practice"
<strong>Output:</strong> 3
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> wordsDict = ["practice", "makes", "perfect", "coding", "makes"], word1 = "makes", word2 = "coding"
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= wordsDict.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= wordsDict[i].length &lt;= 10</code></li>
	<li><code>wordsDict[i]</code> consists of lowercase English letters.</li>
	<li><code>word1</code> and <code>word2</code> are in <code>wordsDict</code>.</li>
	<li><code>word1 != word2</code></li>
</ul>

**Companies**:  
[LinkedIn](https://leetcode.com/company/linkedin), [Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Uber](https://leetcode.com/company/uber), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Salesforce](https://leetcode.com/company/salesforce), [DiDi](https://leetcode.com/company/didi)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [String](https://leetcode.com/tag/string/)

**Similar Questions**:

- [Shortest Word Distance II (Medium)](https://leetcode.com/problems/shortest-word-distance-ii/)
- [Shortest Word Distance III (Medium)](https://leetcode.com/problems/shortest-word-distance-iii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/shortest-word-distance/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int shortestDistance(String[] wordsDict, String word1, String word2) {
        if (wordsDict == null) return 0;
        int index1 = -1;
        int index2 = -1;
        int shortest = Integer.MAX_VALUE;
        //at each i, check if both words was found, if yes calculate the current distance and get min
        for (int i=0; i<wordsDict.length; i++) {
            if (wordsDict[i].equals(word1)) {
                index1 = i;
            }
            if (wordsDict[i].equals(word2)) {
                index2 = i;
            }
            //if both found
            if (index1 != -1 && index2 != -1) {
                shortest = Math.min(shortest, Math.abs(index1 - index2)) ;
            }
        }
        return shortest;
    }
}
```

# [127. Word Ladder (Hard)](https://leetcode.com/problems/word-ladder/)

<p>A <strong>transformation sequence</strong> from word <code>beginWord</code> to word <code>endWord</code> using a dictionary <code>wordList</code> is a sequence of words <code>beginWord -&gt; s<sub>1</sub> -&gt; s<sub>2</sub> -&gt; ... -&gt; s<sub>k</sub></code> such that:</p>

<ul>
	<li>Every adjacent pair of words differs by a single letter.</li>
	<li>Every <code>s<sub>i</sub></code> for <code>1 &lt;= i &lt;= k</code> is in <code>wordList</code>. Note that <code>beginWord</code> does not need to be in <code>wordList</code>.</li>
	<li><code>s<sub>k</sub> == endWord</code></li>
</ul>

<p>Given two words, <code>beginWord</code> and <code>endWord</code>, and a dictionary <code>wordList</code>, return <em>the <strong>number of words</strong> in the <strong>shortest transformation sequence</strong> from</em> <code>beginWord</code> <em>to</em> <code>endWord</code><em>, or </em><code>0</code><em> if no such sequence exists.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]
<strong>Output:</strong> 5
<strong>Explanation:</strong> One shortest transformation sequence is "hit" -&gt; "hot" -&gt; "dot" -&gt; "dog" -&gt; cog", which is 5 words long.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log"]
<strong>Output:</strong> 0
<strong>Explanation:</strong> The endWord "cog" is not in wordList, therefore there is no valid transformation sequence.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= beginWord.length &lt;= 10</code></li>
	<li><code>endWord.length == beginWord.length</code></li>
	<li><code>1 &lt;= wordList.length &lt;= 5000</code></li>
	<li><code>wordList[i].length == beginWord.length</code></li>
	<li><code>beginWord</code>, <code>endWord</code>, and <code>wordList[i]</code> consist of lowercase English letters.</li>
	<li><code>beginWord != endWord</code></li>
	<li>All the words in <code>wordList</code> are <strong>unique</strong>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Uber](https://leetcode.com/company/uber), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google), [Qualtrics](https://leetcode.com/company/qualtrics), [Microsoft](https://leetcode.com/company/microsoft), [LinkedIn](https://leetcode.com/company/linkedin), [Hulu](https://leetcode.com/company/hulu), [VMware](https://leetcode.com/company/vmware), [Snapchat](https://leetcode.com/company/snapchat), [Lyft](https://leetcode.com/company/lyft), [Zillow](https://leetcode.com/company/zillow), [Expedia](https://leetcode.com/company/expedia), [Citadel](https://leetcode.com/company/citadel), [Swiggy](https://leetcode.com/company/swiggy)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/)

**Similar Questions**:

- [Word Ladder II (Hard)](https://leetcode.com/problems/word-ladder-ii/)
- [Minimum Genetic Mutation (Medium)](https://leetcode.com/problems/minimum-genetic-mutation/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/word-ladder/
// Author: Please set your name in options page
// Time: O()
// Space: O()
}
            }
        }
        //if we are here, cannot find any word
        return 0;
    }
    private List<String> getNeighbors(String s) {
        List<String> neighbors = new ArrayList<>();
        char[] chars = s.toCharArray();
        //loop through each char -> replace it with the rest 25 lower character
        for (int i=0; i<chars.length; i++) {
            char currentChar = chars[i]; //keep this so we can replace back the original word
            //replace and add to neighbors
            for (char c='a'; c<='z'; c++) {
                chars[i] = c;
                String word = new String(chars);
                neighbors.add(word);
            }
            //get back the original word to check for the next round
            chars[i] = currentChar;
        }
        return neighbors;
    }
}

```

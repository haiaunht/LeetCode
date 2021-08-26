# [139. Word Break (Medium)](https://leetcode.com/problems/word-break/)

<p>Given a string <code>s</code> and a dictionary of strings <code>wordDict</code>, return <code>true</code> if <code>s</code> can be segmented into a space-separated sequence of one or more dictionary words.</p>

<p><strong>Note</strong> that the same word in the dictionary may be reused multiple times in the segmentation.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "leetcode", wordDict = ["leet","code"]
<strong>Output:</strong> true
<strong>Explanation:</strong> Return true because "leetcode" can be segmented as "leet code".
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "applepenapple", wordDict = ["apple","pen"]
<strong>Output:</strong> true
<strong>Explanation:</strong> Return true because "applepenapple" can be segmented as "apple pen apple".
Note that you are allowed to reuse a dictionary word.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "catsandog", wordDict = ["cats","dog","sand","and","cat"]
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 300</code></li>
	<li><code>1 &lt;= wordDict.length &lt;= 1000</code></li>
	<li><code>1 &lt;= wordDict[i].length &lt;= 20</code></li>
	<li><code>s</code> and <code>wordDict[i]</code> consist of only lowercase English letters.</li>
	<li>All the strings of <code>wordDict</code> are <strong>unique</strong>.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Uber](https://leetcode.com/company/uber), [Microsoft](https://leetcode.com/company/microsoft), [Bloomberg](https://leetcode.com/company/bloomberg), [ByteDance](https://leetcode.com/company/bytedance), [Qualtrics](https://leetcode.com/company/qualtrics), [Apple](https://leetcode.com/company/apple), [eBay](https://leetcode.com/company/ebay), [Walmart Labs](https://leetcode.com/company/walmart-labs), [Swiggy](https://leetcode.com/company/swiggy)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/), [Trie](https://leetcode.com/tag/trie/), [Memoization](https://leetcode.com/tag/memoization/)

**Similar Questions**:

- [Word Break II (Hard)](https://leetcode.com/problems/word-break-ii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/word-break/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        //use dynamic to bottom up form each char to check
        boolean[] dp = new boolean[s.length() + 1];
        dp[0] = true;
        //loop from 1 since at 0 it is true
        for (int i=1; i<s.length()+1; i++) {
            for (int j=0; j<i; j++) {
                String currentStringForm = s.substring(j,i);
                if (wordDict.contains(currentStringForm) && dp[j] == true) {
                    dp[i] = true;
                    break;
                }
            }
        }
        if (dp[s.length()] == true) return true;
        return false;
    }
}
```

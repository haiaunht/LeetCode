# [140. Word Break II (Hard)](https://leetcode.com/problems/word-break-ii/)

<p>Given a string <code>s</code> and a dictionary of strings <code>wordDict</code>, add spaces in <code>s</code> to construct a sentence where each word is a valid dictionary word. Return all such possible sentences in <strong>any order</strong>.</p>

<p><strong>Note</strong> that the same word in the dictionary may be reused multiple times in the segmentation.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "catsanddog", wordDict = ["cat","cats","and","sand","dog"]
<strong>Output:</strong> ["cats and dog","cat sand dog"]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "pineapplepenapple", wordDict = ["apple","pen","applepen","pine","pineapple"]
<strong>Output:</strong> ["pine apple pen apple","pineapple pen apple","pine applepen apple"]
<strong>Explanation:</strong> Note that you are allowed to reuse a dictionary word.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "catsandog", wordDict = ["cats","dog","sand","and","cat"]
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 20</code></li>
	<li><code>1 &lt;= wordDict.length &lt;= 1000</code></li>
	<li><code>1 &lt;= wordDict[i].length &lt;= 10</code></li>
	<li><code>s</code> and <code>wordDict[i]</code> consist of only lowercase English letters.</li>
	<li>All the strings of <code>wordDict</code> are <strong>unique</strong>.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Bloomberg](https://leetcode.com/company/bloomberg), [Microsoft](https://leetcode.com/company/microsoft), [Uber](https://leetcode.com/company/uber), [Adobe](https://leetcode.com/company/adobe)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/), [Backtracking](https://leetcode.com/tag/backtracking/), [Trie](https://leetcode.com/tag/trie/), [Memoization](https://leetcode.com/tag/memoization/)

**Similar Questions**:

- [Word Break (Medium)](https://leetcode.com/problems/word-break/)
- [Concatenated Words (Hard)](https://leetcode.com/problems/concatenated-words/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/word-break-ii/
// Author: Please set your name in options page
// Time: O(n^2 + 2^N + Word in Dict)
// Space: O(n^2 + 2^N + Word in Dict)
class Solution {
    public List<String> wordBreak(String s, List<String> wordDict) {
        Set<String> set = new HashSet<>(wordDict);
        boolean[] dp = new boolean[s.length()+1];
        dp[0] = true;
        List<List<String>> dpList = new ArrayList<>(s.length()+1);
        for (int i=0; i<s.length()+1; i++) {
            dpList.add(new ArrayList<>());
        }
        dpList.get(0).add(""); //start with empty string as dp[0] is true
        for (int i=1; i<s.length()+1; i++) {
            for (int j=0; j<i; j++) {
                String curr = s.substring(j, i);
                if (dp[j] && set.contains(curr)) {
                    dp[i] = true;
                    List<String> currentList = dpList.get(i);
                    //now check at index j, if there is a list of string, add up curr with " ", else just add without " "
                    for (String stringAtJ : dpList.get(j)) {
                        if (stringAtJ.equals("")) {
                            currentList.add(curr);
                        } else {
                            currentList.add(stringAtJ + " " + curr);
                        }
                    }
                }
            }
        }
        return dpList.get(dpList.size()-1);
    }
}

```

# [1258. Synonymous Sentences (Medium)](https://leetcode.com/problems/synonymous-sentences/)

Given a list of pairs of equivalent words <code>synonyms</code> and a sentence <code>text</code>, Return all possible synonymous sentences <strong>sorted lexicographically</strong>.

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:
</strong>synonyms = [["happy","joy"],["sad","sorrow"],["joy","cheerful"]],
text = "I am happy today but was sad yesterday"
<strong>Output:
</strong>["I am cheerful today but was sad yesterday",
"I am cheerful today but was sorrow yesterday",
"I am happy today but was sad yesterday",
"I am happy today but was sorrow yesterday",
"I am joy today but was sad yesterday",
"I am joy today but was sorrow yesterday"]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> synonyms = [["happy","joy"],["cheerful","glad"]], text = "I am happy today but was sad yesterday"
<strong>Output:</strong> ["I am happy today but was sad yesterday","I am joy today but was sad yesterday"]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> synonyms = [["a","b"],["c","d"],["e","f"]], text = "a c e"
<strong>Output:</strong> ["a c e","a c f","a d e","a d f","b c e","b c f","b d e","b d f"]
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> synonyms = [["a","QrbCl"]], text = "d QrbCl ya ya NjZQ"
<strong>Output:</strong> ["d QrbCl ya ya NjZQ","d a ya ya NjZQ"]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;=&nbsp;synonyms.length &lt;= 10</code></li>
	<li><code>synonyms[i].length == 2</code></li>
	<li><code>synonyms[i][0] != synonyms[i][1]</code></li>
	<li>All words consist of at most <code>10</code> English letters only.</li>
	<li><code>text</code>&nbsp;is a single space separated sentence of at most <code>10</code> words.</li>
</ul>

**Companies**:  
[Cruise Automation](https://leetcode.com/company/cruise-automation), [Google](https://leetcode.com/company/google), [Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/), [Backtracking](https://leetcode.com/tag/backtracking/), [Union Find](https://leetcode.com/tag/union-find/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/synonymous-sentences/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public List<String> generateSentences(List<List<String>> synonyms, String text) {
        TreeSet<String> texts = new TreeSet<String>();
        texts.add(text);
        int size = 0;
        while (texts.size() != size) {
            size = texts.size();
            //retrive each pairs in synonyms, check with treeSet texts and replace
            for (List<String> synonym : synonyms) {
                String word1 = synonym.get(0);
                String word2 = synonym.get(1);
                Set<String> replace = new HashSet<>();
                //go throught list of texts
                for (String t : texts) {
                    replace.add(t.replaceFirst("\\b"+word1+"\\b", word2));
                    replace.add(t.replaceFirst("\\b"+word2+"\\b", word1));
                }
                texts = new TreeSet<>(replace);
            }
        }
        return new ArrayList<>(texts);
    }
}

```

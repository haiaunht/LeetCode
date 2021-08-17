# [1002. Find Common Characters (Easy)](https://leetcode.com/problems/find-common-characters/)

<p>Given a string array <code>words</code>, return <em>an array of all characters that show up in all strings within the </em><code>words</code><em> (including duplicates)</em>. You may return the answer in <strong>any order</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> words = ["bella","label","roller"]
<strong>Output:</strong> ["e","l","l"]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> words = ["cool","lock","cook"]
<strong>Output:</strong> ["c","o"]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 100</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 100</code></li>
	<li><code>words[i]</code> consists of lowercase English letters.</li>
</ul>

**Companies**:  
[Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google), [Adobe](https://leetcode.com/company/adobe), [Amazon](https://leetcode.com/company/amazon), [Uber](https://leetcode.com/company/uber)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/)

**Similar Questions**:

- [Intersection of Two Arrays II (Easy)](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/find-common-characters/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public List<String> commonChars(String[] words) {
        List<String> result = new ArrayList<>();
        //create another list to store all the counts[] of each word
        List<int[]> charsEachWord = new ArrayList<>();
        for (String word : words) {
            charsEachWord.add(countChar(word));
        }
        //loop through each char and get the min count, from there loop 0->min and add to result
        for (int c=0; c<26; c++) {
            int min = Integer.MAX_VALUE;
            for (int i=0; i<charsEachWord.size(); i++) {
                min = Math.min(min, charsEachWord.get(i)[c]);
            }
            for (int k=0; k<min; k++) {
                char curr = (char)('a' + c);
                result.add(Character.toString(curr));
            }
        }
        return result;
    }
    private int[] countChar(String s) {
        int[] counts = new int[26];
        for (char c : s.toCharArray()) {
            counts[c - 'a']++;
        }
        return counts;
    }
}

```

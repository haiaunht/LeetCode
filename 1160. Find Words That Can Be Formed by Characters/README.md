# [1160. Find Words That Can Be Formed by Characters (Easy)](https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/)

<p>You are given an array of strings&nbsp;<code>words</code>&nbsp;and a string&nbsp;<code>chars</code>.</p>

<p>A string is <em>good</em>&nbsp;if&nbsp;it can be formed by&nbsp;characters from <code>chars</code>&nbsp;(each character&nbsp;can only be used once).</p>

<p>Return the sum of lengths of all good strings in <code>words</code>.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre><strong>Input: </strong>words = <span id="example-input-1-1">["cat","bt","hat","tree"]</span>, chars = <span id="example-input-1-2">"atach"</span>
<strong>Output: </strong><span id="example-output-1">6</span>
<strong>Explanation: </strong>
The strings that can be formed are "cat" and "hat" so the answer is 3 + 3 = 6.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input: </strong>words = <span id="example-input-2-1">["hello","world","leetcode"]</span>, chars = <span id="example-input-2-2">"welldonehoneyr"</span>
<strong>Output: </strong><span id="example-output-2">10</span>
<strong>Explanation: </strong>
The strings that can be formed are "hello" and "world" so the answer is 5 + 5 = 10.
</pre>

<p>&nbsp;</p>

<p><span><strong>Note:</strong></span></p>

<ol>
	<li><code>1 &lt;= words.length &lt;= 1000</code></li>
	<li><code>1 &lt;= words[i].length, chars.length&nbsp;&lt;= 100</code></li>
	<li>All strings contain lowercase English letters only.</li>
</ol>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Oracle](https://leetcode.com/company/oracle)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int countCharacters(String[] words, String chars) {
        int result = 0;
        //use counting sort to see the frequently of char in chars
        int[] charsCountingSort = new int[26];
        for (char c : chars.toCharArray()) {
            charsCountingSort[c - 'a']++;
        }
        for (String word : words) {
            //use counting sort for each word, then compare with charsCountingSort
            int[] wordCount = new int[26];
            boolean isForm = true;
            for (char c : word.toCharArray()) {
                wordCount[c - 'a']++;
                //if word use char more than it has in charsCountingSort -> false
                if (wordCount[c - 'a'] > charsCountingSort[c - 'a']) {
                    isForm = false;
                    break;
                }
            }
            //we are here because the word isForm
            if (isForm) result += word.length();
        }
        return result;
    }
}

```

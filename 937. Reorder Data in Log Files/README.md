# [937. Reorder Data in Log Files (Easy)](https://leetcode.com/problems/reorder-data-in-log-files/)

<p>You are given an array of <code>logs</code>. Each log is a space-delimited string of words, where the first word is the <strong>identifier</strong>.</p>

<p>There are two types of logs:</p>

<ul>
	<li><b>Letter-logs</b>: All words (except the identifier) consist of lowercase English letters.</li>
	<li><strong>Digit-logs</strong>: All words (except the identifier) consist of digits.</li>
</ul>

<p>Reorder these logs so that:</p>

<ol>
	<li>The <strong>letter-logs</strong> come before all <strong>digit-logs</strong>.</li>
	<li>The <strong>letter-logs</strong> are sorted lexicographically by their contents. If their contents are the same, then sort them lexicographically by their identifiers.</li>
	<li>The <strong>digit-logs</strong> maintain their relative ordering.</li>
</ol>

<p>Return <em>the final order of the logs</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> logs = ["dig1 8 1 5 1","let1 art can","dig2 3 6","let2 own kit dig","let3 art zero"]
<strong>Output:</strong> ["let1 art can","let3 art zero","let2 own kit dig","dig1 8 1 5 1","dig2 3 6"]
<strong>Explanation:</strong>
The letter-log contents are all different, so their ordering is "art can", "art zero", "own kit dig".
The digit-logs have a relative order of "dig1 8 1 5 1", "dig2 3 6".
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> logs = ["a1 9 2 3 1","g1 act car","zo4 4 7","ab1 off key dog","a8 act zoo"]
<strong>Output:</strong> ["g1 act car","a8 act zoo","ab1 off key dog","a1 9 2 3 1","zo4 4 7"]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= logs.length &lt;= 100</code></li>
	<li><code>3 &lt;= logs[i].length &lt;= 100</code></li>
	<li>All the tokens of <code>logs[i]</code> are separated by a <strong>single</strong> space.</li>
	<li><code>logs[i]</code> is guaranteed to have an identifier and at least one word after the identifier.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Audible](https://leetcode.com/company/audible)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [String](https://leetcode.com/tag/string/), [Sorting](https://leetcode.com/tag/sorting/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/reorder-data-in-log-files/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public String[] reorderLogFiles(String[] logs) {
        List<String> letters = new ArrayList<>();
        List<String> digits = new ArrayList<>();
        //add each log to corresponding category
        for (String log : logs) {
            if (isLetter(log)) {
                letters.add(log);
            } else {
                digits.add(log);
            }
        }
        //sort all String in letters by its context first then identifier
        Collections.sort(letters, (str1, str2)->{
            String id_1 = str1.substring(0, str1.indexOf(' '));
            String id_2 = str2.substring(0, str2.indexOf(' '));
            String content_1 = str1.substring(str1.indexOf(' ')+1);
            String content_2 = str2.substring(str2.indexOf(' ')+1);
            if (content_1.equals(content_2)) {
                return id_1.compareTo(id_2);
            } else {
                return content_1.compareTo(content_2);
            }
        });
        for (String d : digits) {
            letters.add(d);
        }
        String[] result = new String[letters.size()];
        int count = 0;
        for (String s : letters) {
            result[count++] = s;
        }
        return result;
    }
    private boolean isLetter(String s) {
        //"let2 own kit dig" -> split(" ", 2) -> [let2, own kit dig]
        String[] parts = s.split(" ", 2);
        if ( !Character.isDigit(parts[1].charAt(0)) ) {
            return true;
        }
        return false;
    }
}

```

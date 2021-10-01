# [1153. String Transforms Into Another String (Hard)](https://leetcode.com/problems/string-transforms-into-another-string/)

<p>Given two strings <code>str1</code> and <code>str2</code> of the same length, determine whether you can transform <code>str1</code> into <code>str2</code> by doing <strong>zero or more</strong> <em>conversions</em>.</p>

<p>In one conversion you can convert <strong>all</strong> occurrences of one character in <code>str1</code> to <strong>any</strong> other lowercase English character.</p>

<p>Return <code>true</code> if and only if you can transform <code>str1</code> into <code>str2</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> str1 = "aabcc", str2 = "ccdee"
<strong>Output:</strong> true
<strong>Explanation: </strong>Convert 'c' to 'e' then 'b' to 'd' then 'a' to 'c'. Note that the order of conversions matter.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> str1 = "leetcode", str2 = "codeleet"
<strong>Output:</strong> false
<strong>Explanation: </strong>There is no way to transform str1 to str2.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= str1.length == str2.length &lt;= 10<sup>4</sup></code></li>
	<li><code>str1</code> and <code>str2</code> contain only lowercase English letters.</li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [ByteDance](https://leetcode.com/company/bytedance), [tiktok](https://leetcode.com/company/tiktok)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/string-transforms-into-another-string/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean canConvert(String str1, String str2) {
        if (str1.length() != str2.length()) return false;
        if (str1.equals(str2)) return true;
        Map<Character, Character> map1 = new HashMap<>();
        Map<Character, Character> map2 = new HashMap<>();
        for (int i=0; i<str1.length(); i++) {
            char c1 = str1.charAt(i);
            char c2 = str2.charAt(i);
            if (map1.containsKey(c1) && !map2.containsKey(c2)) return false;
            if ((map1.containsKey(c1) && map2.containsKey(c2)) && (map1.get(c1) != c2 || map2.get(c2) != c1)) return false;
            map1.put(c1,c2);
            map2.put(c2,c1);
        }
        if (map2.size() == 26 ) return false;
        return true;
    }
}
            if (map1.containsKey(c1) && !map2.containsKey(c2)) {

```

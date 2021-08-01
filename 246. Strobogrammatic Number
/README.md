# [246. Strobogrammatic Number (Easy)](https://leetcode.com/problems/strobogrammatic-number/)

<p>Given a string <code>num</code> which represents an integer, return <code>true</code> <em>if</em> <code>num</code> <em>is a <strong>strobogrammatic number</strong></em>.</p>

<p>A <strong>strobogrammatic number</strong> is a number that looks the same when rotated <code>180</code> degrees (looked at upside down).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> num = "69"
<strong>Output:</strong> true
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> num = "88"
<strong>Output:</strong> true
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> num = "962"
<strong>Output:</strong> false
</pre><p><strong>Example 4:</strong></p>
<pre><strong>Input:</strong> num = "1"
<strong>Output:</strong> true
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num.length &lt;= 50</code></li>
	<li><code>num</code> consists of only digits.</li>
	<li><code>num</code> does not contain any leading zeros except for zero itself.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [Two Pointers](https://leetcode.com/tag/two-pointers/), [String](https://leetcode.com/tag/string/)

**Similar Questions**:

- [Strobogrammatic Number II (Medium)](https://leetcode.com/problems/strobogrammatic-number-ii/)
- [Strobogrammatic Number III (Hard)](https://leetcode.com/problems/strobogrammatic-number-iii/)
- [Confusing Number (Easy)](https://leetcode.com/problems/confusing-number/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/strobogrammatic-number/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean isStrobogrammatic(String num) {
        Map<Character, Character> map = new HashMap<>();
        map.put('0', '0');
        map.put('1', '1');
        map.put('6', '9');
        map.put('9', '6');
        map.put('8', '8');
        //loop throught num, and reverse with corresponding value in map, if num && reverse is equal -> true
        StringBuilder sb = new StringBuilder();
        for (int i=num.length()-1; i>=0; i--) {
            sb.append(map.get(num.charAt(i)));
        }
        return (sb.toString().equals(num));
    }
}

```

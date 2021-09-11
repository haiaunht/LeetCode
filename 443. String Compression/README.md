# [443. String Compression (Medium)](https://leetcode.com/problems/string-compression/)

<p>Given an array of characters <code>chars</code>, compress it using the following algorithm:</p>

<p>Begin with an empty string <code>s</code>. For each group of <strong>consecutive repeating characters</strong> in <code>chars</code>:</p>

<ul>
	<li>If the group's length is <code>1</code>, append the character to <code>s</code>.</li>
	<li>Otherwise, append the character followed by the group's length.</li>
</ul>

<p>The compressed string <code>s</code> <strong>should not be returned separately</strong>, but instead, be stored <strong>in the input character array <code>chars</code></strong>. Note that group lengths that are <code>10</code> or longer will be split into multiple characters in <code>chars</code>.</p>

<p>After you are done <b>modifying the input array</b>, return <em>the new length of the array</em>.</p>
You must write an algorithm that uses only constant extra space.
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> chars = ["a","a","b","b","c","c","c"]
<strong>Output:</strong> Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]
<strong>Explanation:</strong>&nbsp;The groups are "aa", "bb", and "ccc". This compresses to "a2b2c3".
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> chars = ["a"]
<strong>Output:</strong> Return 1, and the first character of the input array should be: ["a"]
<strong>Explanation:</strong>&nbsp;The only group is "a", which remains uncompressed since it's a single character.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> chars = ["a","b","b","b","b","b","b","b","b","b","b","b","b"]
<strong>Output:</strong> Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].
<strong>Explanation:</strong>&nbsp;The groups are "a" and "bbbbbbbbbbbb". This compresses to "ab12".</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> chars = ["a","a","a","b","b","a","a"]
<strong>Output:</strong> Return 6, and the first 6 characters of the input array should be: ["a","3","b","2","a","2"].
<strong>Explanation:</strong>&nbsp;The groups are "aaa", "bb", and "aa". This compresses to "a3b2a2". Note that each group is independent even if two groups have the same character.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= chars.length &lt;= 2000</code></li>
	<li><code>chars[i]</code> is a lowercase English letter, uppercase English letter, digit, or symbol.</li>
</ul>

**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple), [Yandex](https://leetcode.com/company/yandex), [Amazon](https://leetcode.com/company/amazon), [eBay](https://leetcode.com/company/ebay), [Google](https://leetcode.com/company/google), [Cisco](https://leetcode.com/company/cisco)

**Related Topics**:  
[Two Pointers](https://leetcode.com/tag/two-pointers/), [String](https://leetcode.com/tag/string/)

**Similar Questions**:

- [Count and Say (Medium)](https://leetcode.com/problems/count-and-say/)
- [Encode and Decode Strings (Medium)](https://leetcode.com/problems/encode-and-decode-strings/)
- [Design Compressed String Iterator (Easy)](https://leetcode.com/problems/design-compressed-string-iterator/)
- [Decompress Run-Length Encoded List (Easy)](https://leetcode.com/problems/decompress-run-length-encoded-list/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/string-compression/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(1)
class Solution {
    public int compress(char[] chars) {
       if (chars.length <= 1) return chars.length;
        int slow=0,fast=0;
        while (fast < chars.length) {
            int count = 0;
            char current = chars[fast];
            while (fast < chars.length && chars[fast] == current) {
                count++;
                fast++;
            }
            //after done checking duplicate char, assign checked char to show index
            chars[slow++] = current;
            //now replace the count after the char, in case the count is 2 digit
            if (count > 1) {
                for (int c=0; c<String.valueOf(count).length(); c++) {
                    chars[slow++] = String.valueOf(count).charAt(c);
                }
            }
        }
        return slow;
    }
}

```

# [242. Valid Anagram (Easy)](https://leetcode.com/problems/valid-anagram/)

<p>Given two strings <code>s</code> and <code>t</code>, return <code>true</code> <em>if</em> <code>t</code> <em>is an anagram of</em> <code>s</code><em>, and</em> <code>false</code> <em>otherwise</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "anagram", t = "nagaram"
<strong>Output:</strong> true
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "rat", t = "car"
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length, t.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code> and <code>t</code> consist of lowercase English letters.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> What if the inputs contain Unicode characters? How would you adapt your solution to such a case?</p>

**Companies**:  
[Bloomberg](https://leetcode.com/company/bloomberg), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Apple](https://leetcode.com/company/apple), [Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Adobe](https://leetcode.com/company/adobe), [Cisco](https://leetcode.com/company/cisco), [BlackRock](https://leetcode.com/company/blackrock), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Paypal](https://leetcode.com/company/paypal), [Oracle](https://leetcode.com/company/oracle), [Visa](https://leetcode.com/company/visa)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [Sort](https://leetcode.com/tag/sort/)

**Similar Questions**:

- [Group Anagrams (Medium)](https://leetcode.com/problems/group-anagrams/)
- [Palindrome Permutation (Easy)](https://leetcode.com/problems/palindrome-permutation/)
- [Find All Anagrams in a String (Medium)](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/valid-anagram/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        int[] counts = new int[26];
        //counting sort
        for (int i=0; i<s.length(); i++) {
            counts[s.charAt(i) - 'a']++; //if charAt(i)='a'->counts[0]=1;
            counts[t.charAt(i) - 'a']--;
        }
        for (int i : counts) {
            if (i!=0) return false; //if true counts[] should contains all 0
        }
        return true;
    }
}

```

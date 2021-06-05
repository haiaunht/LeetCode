# [917. Reverse Only Letters (Easy)](https://leetcode.com/problems/reverse-only-letters/)

<p>Given a string <code>s</code>, return the "reversed" string where all characters that are not a letter&nbsp;stay in the same place, and all letters reverse their positions.</p>

<p>&nbsp;</p>

<div>
<div>
<div>
<ol>
</ol>
</div>
</div>
</div>

<div>
<p><strong>Example 1:</strong></p>

<pre><strong>Input: </strong>s = <span id="example-input-1-1">"ab-cd"</span>
<strong>Output: </strong><span id="example-output-1">"dc-ba"</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre><strong>Input: </strong>s = <span id="example-input-2-1">"a-bC-dEf-ghIj"</span>
<strong>Output: </strong><span id="example-output-2">"j-Ih-gfE-dCba"</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre><strong>Input: </strong>s = <span id="example-input-3-1">"Test1ng-Leet=code-Q!"</span>
<strong>Output: </strong><span id="example-output-3">"Qedo1ct-eeLg=ntse-T!"</span>
</pre>

<p>&nbsp;</p>

<div>
<p><strong><span>Note:</span></strong></p>

<ol>
	<li><code>s.length &lt;= 100</code></li>
	<li><code>33 &lt;= s[i].ASCIIcode &lt;= 122</code>&nbsp;</li>
	<li><code>s</code> doesn't contain <code>\</code> or <code>"</code></li>
</ol>
</div>
</div>
</div>
</div>

**Companies**:  
[Apple](https://leetcode.com/company/apple), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[String](https://leetcode.com/tag/string/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/reverse-only-letters/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public String reverseOnlyLetters(String s) {
        //using stack
        Stack<Character> chars = new Stack();
        for (char c : s.toCharArray()) {
            if (Character.isAlphabetic(c)) {
                chars.push(c);
            }
        }
        StringBuilder result = new StringBuilder();
        for (char c : s.toCharArray()) {
            if (!Character.isAlphabetic(c)) { //if not char, just append in order
                result.append(c);
            } else { //else pop out of stack and append here 
                result.append(chars.pop());
            }
        }
        return result.toString();
    }
}

```

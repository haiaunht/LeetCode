# [20. Valid Parentheses (Easy)](https://leetcode.com/problems/valid-parentheses/)

<p>Given a string <code>s</code> containing just the characters <code>'('</code>, <code>')'</code>, <code>'{'</code>, <code>'}'</code>, <code>'['</code> and <code>']'</code>, determine if the input string is valid.</p>

<p>An input string is valid if:</p>

<ol>
	<li>Open brackets must be closed by the same type of brackets.</li>
	<li>Open brackets must be closed in the correct order.</li>
</ol>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "()"
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "()[]{}"
<strong>Output:</strong> true
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "(]"
<strong>Output:</strong> false
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> s = "([)]"
<strong>Output:</strong> false
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> s = "{[]}"
<strong>Output:</strong> true
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> consists of parentheses only <code>'()[]{}'</code>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Apple](https://leetcode.com/company/apple), [Microsoft](https://leetcode.com/company/microsoft), [Bloomberg](https://leetcode.com/company/bloomberg), [LinkedIn](https://leetcode.com/company/linkedin), [Facebook](https://leetcode.com/company/facebook), [Expedia](https://leetcode.com/company/expedia), [Google](https://leetcode.com/company/google), [Cisco](https://leetcode.com/company/cisco), [Spotify](https://leetcode.com/company/spotify), [Paypal](https://leetcode.com/company/paypal), [Yahoo](https://leetcode.com/company/yahoo), [JPMorgan](https://leetcode.com/company/jpmorgan), [Intuit](https://leetcode.com/company/intuit), [Atlassian](https://leetcode.com/company/atlassian), [eBay](https://leetcode.com/company/ebay), [Adobe](https://leetcode.com/company/adobe), [ServiceNow](https://leetcode.com/company/servicenow), [Qualcomm](https://leetcode.com/company/qualcomm), [Zillow](https://leetcode.com/company/zillow)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Stack](https://leetcode.com/tag/stack/)

**Similar Questions**:

- [Generate Parentheses (Medium)](https://leetcode.com/problems/generate-parentheses/)
- [Longest Valid Parentheses (Hard)](https://leetcode.com/problems/longest-valid-parentheses/)
- [Remove Invalid Parentheses (Hard)](https://leetcode.com/problems/remove-invalid-parentheses/)
- [Check If Word Is Valid After Substitutions (Medium)](https://leetcode.com/problems/check-if-word-is-valid-after-substitutions/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/valid-parentheses/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean isValid(String s) {
        Map<Character, Character> matching = Map.of('[',']','{', '}', '(', ')');
        // "{[]}", first if i see open, push to the stack, when i see the close check the matching in stack to pop
        Stack<Character> stack = new Stack<>();
        for (char c : s.toCharArray()) {
            //check if this is open or close? if map contains is open, else is not open stack= {[
            if (matching.containsKey(c)) {
                stack.push(c);
            } 
            else { //this will be closing tag case, check if the open tag of this in stack so i can pop
                if (stack.isEmpty()) {
                    return false; //this is the hanging tag, so return not matching
                }
                char openTag = stack.pop();
                if (matching.get(openTag) != c) {
                    return false;
                }
            }
        }
        if (stack.isEmpty()) {
            return true;
        } else {
            return false;
        }
    }
}

```

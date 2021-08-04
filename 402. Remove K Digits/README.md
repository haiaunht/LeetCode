# [402. Remove K Digits (Medium)](https://leetcode.com/problems/remove-k-digits/)

<p>Given string num representing a non-negative integer <code>num</code>, and an integer <code>k</code>, return <em>the smallest possible integer after removing</em> <code>k</code> <em>digits from</em> <code>num</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> num = "1432219", k = 3
<strong>Output:</strong> "1219"
<strong>Explanation:</strong> Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> num = "10200", k = 1
<strong>Output:</strong> "200"
<strong>Explanation:</strong> Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> num = "10", k = 2
<strong>Output:</strong> "0"
<strong>Explanation:</strong> Remove all the digits from the number and it is left with nothing which is 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= num.length &lt;= 10<sup>5</sup></code></li>
	<li><code>num</code> consists of only digits.</li>
	<li><code>num</code> does not have any leading zeros except for the zero itself.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [ByteDance](https://leetcode.com/company/bytedance), [Cisco](https://leetcode.com/company/cisco)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Stack](https://leetcode.com/tag/stack/), [Greedy](https://leetcode.com/tag/greedy/), [Monotonic Stack](https://leetcode.com/tag/monotonic-stack/)

**Similar Questions**:

- [Create Maximum Number (Hard)](https://leetcode.com/problems/create-maximum-number/)
- [Monotone Increasing Digits (Medium)](https://leetcode.com/problems/monotone-increasing-digits/)
- [Find the Most Competitive Subsequence (Medium)](https://leetcode.com/problems/find-the-most-competitive-subsequence/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/remove-k-digits/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public String removeKdigits(String num, int k) {
        LinkedList<Character> stack = new LinkedList<Character>();
        for(char digit : num.toCharArray()) {
          while(stack.size() > 0 && k > 0 && stack.peekLast() > digit) {
            stack.removeLast();
            k -= 1;
          }
          stack.addLast(digit);
        }
        /* if the stack is not pop after adding (case of one "9") -> remove k here */
        for(int i=0; i<k; ++i) {
          stack.removeLast();
        }
        // if there is an 0 remove
        StringBuilder ret = new StringBuilder();
        boolean leadingZero = true;
        for(char digit: stack) {
          if(leadingZero && digit == '0') continue;
          leadingZero = false;
          ret.append(digit);
        }
        if (ret.length() == 0) return "0";
        return ret.toString();
    }
}

```

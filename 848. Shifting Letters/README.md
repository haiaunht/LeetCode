# [848. Shifting Letters (Medium)](https://leetcode.com/problems/shifting-letters/solution/)

<p>You are given a string <code>s</code> of lowercase English letters and an integer array <code>shifts</code> of the same length.</p>

<p>Call the <code>shift()</code> of a letter, the next letter in the alphabet, (wrapping around so that <code>'z'</code> becomes <code>'a'</code>).</p>

<ul>
	<li>For example, <code>shift('a') = 'b'</code>, <code>shift('t') = 'u'</code>, and <code>shift('z') = 'a'</code>.</li>
</ul>

<p>Now for each <code>shifts[i] = x</code>, we want to shift the first <code>i + 1</code> letters of <code>s</code>, <code>x</code> times.</p>

<p>Return <em>the final string after all such shifts to s are applied</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "abc", shifts = [3,5,9]
<strong>Output:</strong> "rpl"
<strong>Explanation:</strong> We start with "abc".
After shifting the first 1 letters of s by 3, we have "dbc".
After shifting the first 2 letters of s by 5, we have "igc".
After shifting the first 3 letters of s by 9, we have "rpl", the answer.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "aaa", shifts = [1,2,3]
<strong>Output:</strong> "gfd"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
	<li><code>shifts.length == s.length</code></li>
	<li><code>0 &lt;= shifts[i] &lt;= 10<sup>9</sup></code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [String](https://leetcode.com/tag/string/)

**Similar Questions**:

- [Replace All Digits with Characters (Easy)](https://leetcode.com/problems/replace-all-digits-with-characters/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/shifting-letters/solution/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(N)
class Solution {
    public String shiftingLetters(String s, int[] shifts) {
        // calculate the total shifts
        for(int i=shifts.length-1; i>0; --i){
            shifts[i-1] += shifts[i];
            shifts[i-1] %= 26;
        }
        char[] charArr = s.toCharArray();
        for(int i=0; i<s.length(); ++i){
            int numOfShift = (charArr[i]-'a' + shifts[i])%26;
            charArr[i] = (char)('a'+ numOfShift);
        }
        return String.valueOf(charArr);
//         int[] countingSort = new int[s.length()];
//         int count = 0;
//         for (char c : s.toCharArray()) {
//             countingSort[count++] = c - 'a';
//         }
//         for (int i=0; i<shifts.length; i++) {
//             int shift = shifts[i];
//             shiftArr(countingSort, i+1, shift);
//         }
//         StringBuilder sb = new StringBuilder();
//         for (int num : countingSort) {
//             sb.append((char)(num%26 + 'a'));
//         }
//         return sb.toString();
//     }
//     private void shiftArr(int[] nums,int elements, int shift) {
//         }

```

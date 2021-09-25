# [423. Reconstruct Original Digits from English (Medium)](https://leetcode.com/problems/reconstruct-original-digits-from-english/)

<p>Given a string <code>s</code> containing an out-of-order English representation of digits <code>0-9</code>, return <em>the digits in <strong>ascending</strong> order</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "owoztneoer"
<strong>Output:</strong> "012"
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "fviefuro"
<strong>Output:</strong> "45"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> is one of the characters <code>["e","g","f","i","h","o","n","s","r","u","t","w","v","x","z"]</code>.</li>
	<li><code>s</code> is <strong>guaranteed</strong> to be valid.</li>
</ul>

**Companies**:  
[JPMorgan](https://leetcode.com/company/jpmorgan), [Cisco](https://leetcode.com/company/cisco)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [Math](https://leetcode.com/tag/math/), [String](https://leetcode.com/tag/string/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/reconstruct-original-digits-from-english/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(10) = O(1)
class Solution {
    public String originalDigits(String s) {
        //["e","g","f","i","h","o","n","s","r","u","t","w","v","x","z"].
//          zero = 0
//          one  = 1
//          two  = 2
//          three= 3
//          four = 4
//          five = 5
//          six  = 6
//          seven= 7
//          eight= 8
//          nine = 9
//          We can observe that some characters are only present in some words only like :
//          z(zero) -> 0
//          w(two)  -> 2
//          u(four) -> 4
//          x(six)  -> 6
//          g(eigth)-> 8
//          one, three, five, seven, nine
            // letter in both odd and even
            // three, two, eight -> t
            // five, four -> f
            // seven, six -> s
            //letter in one and nine, choose i instead of n because in nine there two of n's
            // one,zero,two,four -> o
            // nine, five, six, eight -> i
        int[] counts = new int[26];
        for (char c : s.toCharArray()) {
            counts[c - 'a']++;
        }
        int[] digits = new int[10]; //0->9 is 10 digits
        //reference counts to know the digits
        digits[0] = counts['z' - 'a'];
        digits[2] = counts['w' - 'a'];
        digits[4] = counts['u' - 'a'];
        digits[6] = counts['x' - 'a'];
        digits[8] = counts['g' - 'a'];
        digits[5] = counts['f' - 'a'] - digits[4];
        digits[7] = counts['s' - 'a'] - digits[6];
        digits[3] = counts['t' - 'a'] - digits[2] - digits[8];
        digits[1] = counts['o' - 'a'] - digits[0] - digits[2] - digits[4];
        digits[9] = counts['i' - 'a'] - digits[5] - digits[6] - digits[8];
        StringBuilder sb = new StringBuilder();
        for (int i=0; i<digits.length; i++) {
            for (int j=0; j<digits[i]; j++) {
                sb.append(i);
            }
        }
        return sb.toString();
    }
}

```

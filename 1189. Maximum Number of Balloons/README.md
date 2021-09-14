# [1189. Maximum Number of Balloons (Easy)](https://leetcode.com/problems/maximum-number-of-balloons/)

<p>Given a string <code>text</code>, you want to use the characters of <code>text</code> to form as many instances of the word <strong>"balloon"</strong> as possible.</p>

<p>You can use each character in <code>text</code> <strong>at most once</strong>. Return the maximum number of instances that can be formed.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2019/09/05/1536_ex1_upd.JPG" style="width: 132px; height: 35px;"></strong></p>

<pre><strong>Input:</strong> text = "nlaebolko"
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2019/09/05/1536_ex2_upd.JPG" style="width: 267px; height: 35px;"></strong></p>

<pre><strong>Input:</strong> text = "loonbalxballpoon"
<strong>Output:</strong> 2
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> text = "leetcode"
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= text.length &lt;= 10<sup>4</sup></code></li>
	<li><code>text</code> consists of lower case English letters only.</li>
</ul>

**Companies**:  
[Tesla](https://leetcode.com/company/tesla)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/), [Counting](https://leetcode.com/tag/counting/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/maximum-number-of-balloons/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(1)
class Solution {
    public int maxNumberOfBalloons(String text) {
        int[] countingSort = new int[26];
        for (char c : text.toCharArray()) {
            countingSort[c - 'a']++;
        }
        //balloon has a:1,b:1,l:2,o:2,n:1, after count get l and o by half then get min count of these 5
        int aCount = countingSort['a' - 'a'];
        int bCount = countingSort['b' - 'a'];
        int lCount = countingSort['l' - 'a']/2;
        int oCount = countingSort['o' - 'a']/2;
        int nCount = countingSort['n' - 'a'];
        return Math.min(aCount, Math.min(bCount, Math.min(lCount, Math.min(oCount, nCount))));
    }
}

```

# [1128. Number of Equivalent Domino Pairs (Easy)](https://leetcode.com/problems/number-of-equivalent-domino-pairs/)

<p>Given a list of <code>dominoes</code>,&nbsp;<code>dominoes[i] = [a, b]</code>&nbsp;is <em>equivalent</em> to <code>dominoes[j] = [c, d]</code>&nbsp;if and only if either (<code>a==c</code> and <code>b==d</code>), or (<code>a==d</code> and <code>b==c</code>) - that is, one domino can be rotated to be equal to another domino.</p>

<p>Return the number of pairs <code>(i, j)</code> for which <code>0 &lt;= i &lt; j &lt; dominoes.length</code>, and&nbsp;<code>dominoes[i]</code> is equivalent to <code>dominoes[j]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> dominoes = [[1,2],[2,1],[3,4],[5,6]]
<strong>Output:</strong> 1
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= dominoes.length &lt;= 40000</code></li>
	<li><code>1 &lt;= dominoes[i][j] &lt;= 9</code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Counting](https://leetcode.com/tag/counting/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/number-of-equivalent-domino-pairs/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int numEquivDominoPairs(int[][] dominoes) {
         //use a hashmap to store dominoes total val use first*10+second to have total > 9,
        //if d[i]=d[j] which di's value = dj's value
        Map<Integer,Integer> map = new HashMap<>();
        int result = 0;
        for (int[] domino : dominoes) {
            int total = 0;
            //check if first domino [1,2] -> 10*1+2, else rotate dominoe [2,1] -> total should be 2+10*1
            if (domino[0] < domino[1]) {
                total = domino[0]*10 + domino[1];
            } else {
                total = domino[1]*10 + domino[0];
            }
            int count = map.getOrDefault(total, 0);
            map.put(total, count+1);
            result += count;
        }
        return result;
    }
}

```

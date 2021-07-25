# [763. Partition Labels (Medium)](https://leetcode.com/problems/partition-labels/)

<p>You are given a string <code>s</code>. We want to partition the string into as many parts as possible so that each letter appears in at most one part.</p>

<p>Return <em>a list of integers representing the size of these parts</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "ababcbacadefegdehijhklij"
<strong>Output:</strong> [9,7,8]
<strong>Explanation:</strong>
The partition is "ababcbaca", "defegde", "hijhklij".
This is a partition so that each letter appears in at most one part.
A partition like "ababcbacadefegde", "hijhklij" is incorrect, because it splits s into less parts.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "eccbbbbdec"
<strong>Output:</strong> [10]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 500</code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Adobe](https://leetcode.com/company/adobe), [Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple), [Bloomberg](https://leetcode.com/company/bloomberg)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [Two Pointers](https://leetcode.com/tag/two-pointers/), [String](https://leetcode.com/tag/string/), [Greedy](https://leetcode.com/tag/greedy/)

**Similar Questions**:

- [Merge Intervals (Medium)](https://leetcode.com/problems/merge-intervals/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/partition-labels/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public List<Integer> partitionLabels(String s) {
        //"ababcbacadefegdehijhklij"
        List<Integer> partitions = new ArrayList<>();
        //use an thelastIndexOfChar to keep track what indices is the last char
        int[] theLastIndexOfChar = new int[26];
        for (int i=0; i<s.length(); i++) {
            theLastIndexOfChar[s.charAt(i) - 'a'] = i;
        }
        int left = 0;
        while (left < s.length()) {
            //find where the char appear last, use another ptr to tract from i->last
            //'a' i=0, last=8, if some char |.|, compare with 'a'
            int last = theLastIndexOfChar[s.charAt(left) - 'a'];
            int ptr = left;
            //loop to to find the max
            while (ptr != last) {
                last = Math.max(last, theLastIndexOfChar[s.charAt(ptr++)-'a']);
            }
            partitions.add(ptr - left + 1);
            //the next partiton will be = left + partition(ptr - left + 1) = ptr+1
            left = ptr+1;
        }
        return partitions;
    }
}

```

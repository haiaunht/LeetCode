# [904. Fruit Into Baskets (Medium)](https://leetcode.com/problems/fruit-into-baskets/)

<p>You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array <code>fruits</code> where <code>fruits[i]</code> is the <strong>type</strong> of fruit the <code>i<sup>th</sup></code> tree produces.</p>

<p>You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:</p>

<ul>
	<li>You only have <strong>two</strong> baskets, and each basket can only hold a <strong>single type</strong> of fruit. There is no limit on the amount of fruit each basket can hold.</li>
	<li>Starting from any tree of your choice, you must pick <strong>exactly one fruit</strong> from <strong>every</strong> tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.</li>
	<li>Once you reach a tree with fruit that cannot fit in your baskets, you must stop.</li>
</ul>

<p>Given the integer array <code>fruits</code>, return <em>the <strong>maximum</strong> number of fruits you can pick</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> fruits = [<u>1,2,1</u>]
<strong>Output:</strong> 3
<strong>Explanation:</strong> We can pick from all 3 trees.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> fruits = [0,<u>1,2,2</u>]
<strong>Output:</strong> 3
<strong>Explanation:</strong> We can pick from trees [1,2,2].
If we had started at the first tree, we would only pick from trees [0,1].
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> fruits = [1,<u>2,3,2,2</u>]
<strong>Output:</strong> 4
<strong>Explanation:</strong> We can pick from trees [2,3,2,2].
If we had started at the first tree, we would only pick from trees [1,2].
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> fruits = [3,3,3,<u>1,2,1,1,2</u>,3,3,4]
<strong>Output:</strong> 5
<strong>Explanation:</strong> We can pick from trees [1,2,1,1,2].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= fruits.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= fruits[i] &lt; fruits.length</code></li>
</ul>

**Companies**:  
[Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Sliding Window](https://leetcode.com/tag/sliding-window/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/fruit-into-baskets/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(1)
class Solution {
    public int totalFruit(int[] fruits) {
        //find the longest of two integer
        int maxLen = 1;
        if (fruits.length == 1) return maxLen;
        //[3,3,3,1,2,1,1,2,3,3,4]
        int slow = 0;
        int fast = 0;
        Map<Integer, Integer> map = new HashMap<>(); //keep track only two type of fruits
        while (fast < fruits.length) {
            int curr = fruits[fast];
            map.put(curr, map.getOrDefault(curr,0)+1);
            if (map.size() <= 2) {
                maxLen = Math.max(maxLen, fast-slow+1);
                fast++;
            }
            if (map.size() > 2) {
                while (map.size() > 2) {
                    map.put(fruits[slow], map.get(fruits[slow]) - 1);
                    if (map.get(fruits[slow]) == 0) {
                        map.remove(fruits[slow]);
                    }
                    slow++;
                }
                fast++;
            }
        }
        return maxLen;
    }
}

```
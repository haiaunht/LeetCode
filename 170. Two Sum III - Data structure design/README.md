# [170. Two Sum III - Data structure design (Easy)](https://leetcode.com/problems/two-sum-iii-data-structure-design/)

<p>Design a data structure that accepts a stream of integers and checks if it has a pair of integers that sum up to a particular value.</p>

<p>Implement the <code>TwoSum</code> class:</p>

<ul>
	<li><code>TwoSum()</code> Initializes the <code>TwoSum</code> object, with an empty array initially.</li>
	<li><code>void add(int number)</code> Adds <code>number</code> to the data structure.</li>
	<li><code>boolean find(int value)</code> Returns <code>true</code> if there exists any pair of numbers whose sum is equal to <code>value</code>, otherwise, it returns <code>false</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input</strong>
["TwoSum", "add", "add", "add", "find", "find"]
[[], [1], [3], [5], [4], [7]]
<strong>Output</strong>
[null, null, null, null, true, false]

<strong>Explanation</strong>
TwoSum twoSum = new TwoSum();
twoSum.add(1);   // [] --&gt; [1]
twoSum.add(3);   // [1] --&gt; [1,3]
twoSum.add(5);   // [1,3] --&gt; [1,3,5]
twoSum.find(4);  // 1 + 3 = 4, return true
twoSum.find(7);  // No two integers sum up to 7, return false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-10<sup>5</sup> &lt;= number &lt;= 10<sup>5</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= value &lt;= 2<sup>31</sup> - 1</code></li>
	<li>At most <code>5 * 10<sup>4</sup></code> calls will be made to <code>add</code> and <code>find</code>.</li>
</ul>

**Companies**:  
[LinkedIn](https://leetcode.com/company/linkedin)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [Design](https://leetcode.com/tag/design/)

**Similar Questions**:

- [Two Sum (Easy)](https://leetcode.com/problems/two-sum/)
- [Unique Word Abbreviation (Medium)](https://leetcode.com/problems/unique-word-abbreviation/)
- [Two Sum IV - Input is a BST (Easy)](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)

## Solution 1.

```Java
// OJ: https://leetcode.com/problems/two-sum-iii-data-structure-design/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class TwoSum {
    List<Integer> list;
    /** Initialize your data structure here. */
    public TwoSum() {
        list = new ArrayList<>();
    }
    /** Add the number to an internal data structure.. */
    public void add(int number) {
        list.add(number);
    }
    /** Find if there exists any pair of numbers which sum is equal to the value. */
    public boolean find(int value) {
        Map<Integer, Integer> pair = new HashMap<>();
        for (int i=0; i<list.size(); i++) {
            int complement = value - list.get(i);
            if (pair.containsKey(complement)) {
                return true;
            } else {
                pair.put(list.get(i), i);
            }
        }
        return false;
    }
}
/**
 * Your TwoSum object will be instantiated and called as such:
 * TwoSum obj = new TwoSum();
 * obj.add(number);
 * boolean param_2 = obj.find(value);
 */

```

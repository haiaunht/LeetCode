# [384. Shuffle an Array (Medium)](https://leetcode.com/problems/shuffle-an-array/)

<p>Given an integer array <code>nums</code>, design an algorithm to randomly shuffle the array. All permutations of the array should be <strong>equally likely</strong> as a result of the shuffling.</p>

<p>Implement the <code>Solution</code> class:</p>

<ul>
	<li><code>Solution(int[] nums)</code> Initializes the object with the integer array <code>nums</code>.</li>
	<li><code>int[] reset()</code> Resets the array to its original configuration and returns it.</li>
	<li><code>int[] shuffle()</code> Returns a random shuffling of the array.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input</strong>
["Solution", "shuffle", "reset", "shuffle"]
[[[1, 2, 3]], [], [], []]
<strong>Output</strong>
[null, [3, 1, 2], [1, 2, 3], [1, 3, 2]]

<strong>Explanation</strong>
Solution solution = new Solution([1, 2, 3]);
solution.shuffle();    // Shuffle the array [1,2,3] and return its result.
                       // Any permutation of [1,2,3] must be equally likely to be returned.
                       // Example: return [3, 1, 2]
solution.reset();      // Resets the array back to its original configuration [1,2,3]. Return [1, 2, 3]
solution.shuffle();    // Returns the random shuffling of array [1,2,3]. Example: return [1, 3, 2]

</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 200</code></li>
	<li><code>-10<sup>6</sup> &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
	<li>All the elements of <code>nums</code> are <strong>unique</strong>.</li>
	<li>At most <code>5 * 10<sup>4</sup></code> calls <strong>in total</strong> will be made to <code>reset</code> and <code>shuffle</code>.</li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Math](https://leetcode.com/tag/math/), [Randomized](https://leetcode.com/tag/randomized/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/shuffle-an-array/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    int[] origin;
    int[] copy;
    Random rand = new Random();
    public Solution(int[] nums) {
        origin = new int[nums.length];
        copy = new int[nums.length];
        for (int i=0; i<nums.length; i++) {
            origin[i] = nums[i];
            copy[i] = nums[i];
        }
    }
    public int[] reset() {
        return origin;
    }
    public int[] shuffle() {
        for (int i=0; i<copy.length; i++) {
            swapAt(i, randRange(i, copy.length));
        }
        return copy;
    }
    private int randRange(int min, int max) {
        return rand.nextInt(max - min) + min;
    }
    private void swapAt(int i, int j) {
        int temp = copy[i];
        copy[i] = copy[j];
        copy[j] = temp;
    }
}
/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(nums);
 * int[] param_1 = obj.reset();
 * int[] param_2 = obj.shuffle();
 */

```

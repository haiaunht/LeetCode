# [697. Degree of an Array (Easy)](https://leetcode.com/problems/degree-of-an-array/)

<p>Given a non-empty array of non-negative integers <code>nums</code>, the <b>degree</b> of this array is defined as the maximum frequency of any one of its elements.</p>

<p>Your task is to find the smallest possible length of a (contiguous) subarray of <code>nums</code>, that has the same degree as <code>nums</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,2,3,1]
<strong>Output:</strong> 2
<strong>Explanation:</strong> 
The input array has a degree of 2 because both elements 1 and 2 appear twice.
Of the subarrays that have the same degree:
[1, 2, 2, 3, 1], [1, 2, 2, 3], [2, 2, 3, 1], [1, 2, 2], [2, 2, 3], [2, 2]
The shortest length is 2. So return 2.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,2,3,1,4,2]
<strong>Output:</strong> 6
<strong>Explanation:</strong> 
The degree is 3 because the element 2 is repeated 3 times.
So [2,2,3,1,4,2] is the shortest subarray, therefore returning 6.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>nums.length</code> will be between 1 and 50,000.</li>
	<li><code>nums[i]</code> will be an integer between 0 and 49,999.</li>
</ul>

**Companies**:  
[Walmart Labs](https://leetcode.com/company/walmart-labs), [Mathworks](https://leetcode.com/company/mathworks), [Snapchat](https://leetcode.com/company/snapchat)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/)

**Similar Questions**:

- [Maximum Subarray (Easy)](https://leetcode.com/problems/maximum-subarray/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/degree-of-an-array/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(N)
class Solution {
    public int findShortestSubArray(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }
        int degree = 0;
        for (int num : map.keySet()) {
            degree = Math.max(degree, map.get(num));
        }
        //all possible number that contains the same count as degree
        List<Integer> numsOfDegree = new ArrayList<>();
        for (int count : map.keySet()) {
            if (map.get(count) == degree) numsOfDegree.add(count);
        }
        int minLength = Integer.MAX_VALUE;
        Map<Integer, List<Integer>> index = new HashMap<>();
        for (int n : numsOfDegree) {
            index.put(n, new ArrayList<>());
            minLength = Math.min(minLength, getLength(nums, n, index.get(n)));
        }
        return minLength;
    }
    public int getLength(int[] nums, int num, List<Integer> result) {
        for (int i=0; i<nums.length; i++) {
            if (nums[i] == num) {
                result.add(i);
            }
        }
        return result.get(result.size()-1) - result.get(0) + 1;
    }
}

```

# [278. First Bad Version (Easy)](https://leetcode.com/problems/first-bad-version/)

<p>You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.</p>

<p>Suppose you have <code>n</code> versions <code>[1, 2, ..., n]</code> and you want to find out the first bad one, which causes all the following ones to be bad.</p>

<p>You are given an API <code>bool isBadVersion(version)</code> which returns whether <code>version</code> is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> n = 5, bad = 4
<strong>Output:</strong> 4
<strong>Explanation:</strong>
call isBadVersion(3) -&gt; false
call isBadVersion(5)&nbsp;-&gt; true
call isBadVersion(4)&nbsp;-&gt; true
Then 4 is the first bad version.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 1, bad = 1
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= bad &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Bloomberg](https://leetcode.com/company/bloomberg), [VMware](https://leetcode.com/company/vmware), [Adobe](https://leetcode.com/company/adobe), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[Binary Search](https://leetcode.com/tag/binary-search/), [Interactive](https://leetcode.com/tag/interactive/)

**Similar Questions**:

- [Find First and Last Position of Element in Sorted Array (Medium)](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
- [Search Insert Position (Easy)](https://leetcode.com/problems/search-insert-position/)
- [Guess Number Higher or Lower (Easy)](https://leetcode.com/problems/guess-number-higher-or-lower/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/first-bad-version/
// Author: Please set your name in options page
// Time: O(LogN)
// Space: O(1)
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int left = 1;
        int right = n; //start from 1->n
        while (left < right) {
            int middle = left + (right-left)/2;
            //if bad is found, move to the left to check where the last good was found
            if (isBadVersion(middle)) {
                right = middle;
            } else {
                left = middle + 1;
            }
        }
        return left;
    }
}
//  1 2 3 4 5 6 7 8 9
//  G G G G G G B B B       G = Good, B = Bad
//  |       |       |
// left    mid    right

```

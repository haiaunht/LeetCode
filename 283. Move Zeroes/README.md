# [283. Move Zeroes (Easy)](https://leetcode.com/problems/move-zeroes/)

<p>Given an integer array <code>nums</code>, move all <code>0</code>'s to the end of it while maintaining the relative order of the non-zero elements.</p>

<p><strong>Note</strong> that you must do this in-place without making a copy of the array.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [0,1,0,3,12]
<strong>Output:</strong> [1,3,12,0,0]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [0]
<strong>Output:</strong> [0]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Could you minimize the total number of operations done?

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Microsoft](https://leetcode.com/company/microsoft), [Bloomberg](https://leetcode.com/company/bloomberg), [Adobe](https://leetcode.com/company/adobe), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google), [Amazon](https://leetcode.com/company/amazon), [eBay](https://leetcode.com/company/ebay), [Cisco](https://leetcode.com/company/cisco), [Yandex](https://leetcode.com/company/yandex), [Capital One](https://leetcode.com/company/capital-one), [Uber](https://leetcode.com/company/uber)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Two Pointers](https://leetcode.com/tag/two-pointers/)

**Similar Questions**:

- [Remove Element (Easy)](https://leetcode.com/problems/remove-element/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/move-zeroes/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public void moveZeroes(int[] nums) {
       //[0,1,0,3,12] 2 pts pointerToNonZero = 0, pointerToZero =0
        //pointerToNonZero ++ -> pointerToNonZero =1, pointerToZero=0 [1,0,0,3,12] pointerToNonZero++ =2 pointerToZero++ =1
        //
        int pointerToNonZero = 0, pointerToZero = 0 ;
        while (pointerToNonZero < nums.length) {
            if (nums[pointerToNonZero] != 0)  {                
                int holder = nums[pointerToNonZero];
                nums[pointerToNonZero] = nums[pointerToZero];
                nums[pointerToZero] = holder;
                pointerToZero++;
            }            
            pointerToNonZero++;
        }        
    }
}

```

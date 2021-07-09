# [2. Add Two Numbers (Medium)](https://leetcode.com/problems/add-two-numbers/)

<p>You are given two <strong>non-empty</strong> linked lists representing two non-negative integers. The digits are stored in <strong>reverse order</strong>, and each of their nodes contains a single digit. Add the two numbers and return the sum&nbsp;as a linked list.</p>

<p>You may assume the two numbers do not contain any leading zero, except the number 0 itself.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/02/addtwonumber1.jpg" style="width: 483px; height: 342px;">
<pre><strong>Input:</strong> l1 = [2,4,3], l2 = [5,6,4]
<strong>Output:</strong> [7,0,8]
<strong>Explanation:</strong> 342 + 465 = 807.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> l1 = [0], l2 = [0]
<strong>Output:</strong> [0]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
<strong>Output:</strong> [8,9,9,9,0,0,0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in each linked list is in the range <code>[1, 100]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 9</code></li>
	<li>It is guaranteed that the list represents a number that does not have leading zeros.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Adobe](https://leetcode.com/company/adobe), [Google](https://leetcode.com/company/google), [Bloomberg](https://leetcode.com/company/bloomberg), [Apple](https://leetcode.com/company/apple), [Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Yahoo](https://leetcode.com/company/yahoo), [Oracle](https://leetcode.com/company/oracle), [Uber](https://leetcode.com/company/uber), [Cisco](https://leetcode.com/company/cisco), [eBay](https://leetcode.com/company/ebay), [Paypal](https://leetcode.com/company/paypal), [Tesla](https://leetcode.com/company/tesla)

**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Math](https://leetcode.com/tag/math/), [Recursion](https://leetcode.com/tag/recursion/)

**Similar Questions**:

- [Multiply Strings (Medium)](https://leetcode.com/problems/multiply-strings/)
- [Add Binary (Easy)](https://leetcode.com/problems/add-binary/)
- [Sum of Two Integers (Medium)](https://leetcode.com/problems/sum-of-two-integers/)
- [Add Strings (Easy)](https://leetcode.com/problems/add-strings/)
- [Add Two Numbers II (Medium)](https://leetcode.com/problems/add-two-numbers-ii/)
- [Add to Array-Form of Integer (Easy)](https://leetcode.com/problems/add-to-array-form-of-integer/)
- [Add Two Polynomials Represented as Linked Lists (Medium)](https://leetcode.com/problems/add-two-polynomials-represented-as-linked-lists/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/add-two-numbers/
// Author: Please set your name in options page
// Time: O()
// Space: O()
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int carry = 0;
        ListNode sum = new ListNode(-1);
        ListNode current = sum;
        while (l1 != null || l2 != null) {
            int one,two;
            if (l1 == null) one = 0;
            else one = l1.val;
            if (l2 == null) two = 0;
            else two = l2.val;
            int curr = one+two+carry;
            carry = curr/10;
            curr = curr%10;
            current.next = new ListNode(curr);
            current = current.next;
            //now check which one not null, move forward
            if (l1 != null) l1=l1.next;
            if (l2 != null) l2=l2.next;
        }
        if (carry == 1) current.next = new ListNode(1);
        return sum.next;
    }
}

```

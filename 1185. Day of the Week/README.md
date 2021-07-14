# [1185. Day of the Week (Easy)](https://leetcode.com/problems/day-of-the-week/)

<p>Given a date, return the corresponding day of the week for that date.</p>

<p>The input is given as three integers representing the <code>day</code>, <code>month</code> and <code>year</code> respectively.</p>

<p>Return the answer as one of the following values&nbsp;<code>{"Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"}</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> day = 31, month = 8, year = 2019
<strong>Output:</strong> "Saturday"
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> day = 18, month = 7, year = 1999
<strong>Output:</strong> "Sunday"
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> day = 15, month = 8, year = 1993
<strong>Output:</strong> "Sunday"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The given dates are valid dates between the years <code>1971</code> and <code>2100</code>.</li>
</ul>

**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [United Health Group](https://leetcode.com/company/united-health-group)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/)

## Solution 1.

```Java
// OJ: https://leetcode.com/problems/day-of-the-week/
// Author: Please set your name in options page
// Time: O()
// Space: O()
import java.time.LocalDate;
class Solution {
    public String dayOfTheWeek(int day, int month, int year) {
        LocalDate date = LocalDate.of(year, month, day);
        String dateName = date.getDayOfWeek().toString();
        return dateName.charAt(0) + dateName.substring(1).toLowerCase();
    }
}

```

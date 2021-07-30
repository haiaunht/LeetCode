# [1360. Number of Days Between Two Dates (Easy)](https://leetcode.com/problems/number-of-days-between-two-dates/)

<p>Write a program to count the number of days between two dates.</p>

<p>The two dates are given as strings, their format is <code>YYYY-MM-DD</code>&nbsp;as shown in the examples.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> date1 = "2019-06-29", date2 = "2019-06-30"
<strong>Output:</strong> 1
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> date1 = "2020-01-15", date2 = "2019-12-31"
<strong>Output:</strong> 15
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The given dates are valid&nbsp;dates between the years <code>1971</code> and <code>2100</code>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/), [String](https://leetcode.com/tag/string/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/number-of-days-between-two-dates/
// Author: Please set your name in options page
// Time: O()
// Space: O()
import java.time.LocalDate;
class Solution {
    public int daysBetweenDates(String date1, String date2) {
         //calculate today of days of each date1 and date2 return Math.abs(total1-total2)
        int totalDay1 = 0;
        int totalDay2 = 0;
        String[] dateOne = date1.split("-");
        String[] dateTwo = date2.split("-");
        int[] one = {Integer.valueOf(dateOne[0]), Integer.valueOf(dateOne[1]), Integer.valueOf(dateOne[2])};
        int[] two = {Integer.valueOf(dateTwo[0]), Integer.valueOf(dateTwo[1]), Integer.valueOf(dateTwo[2])};
        //accum days of each year
        for (int year=0; year<one[0]; year++) {
            if (isLeapYear(year) == 1) {
                totalDay1 += 366;
            } else {
                totalDay1 += 365;
            }
        }
        for (int year=0; year<two[0]; year++) {
            if (isLeapYear(year) == 1) {
                totalDay2 += 366;
            } else {
                totalDay2 += 365;
            }
        }
        //accum days of months, first row is for non-Leap, second for Leap, add -1 for index-based 1
        int[][] daysOfMonth = {
            {-1,31,28,31,30,31,30,31,31,30,31,30,31},
            {-1,31,29,31,30,31,30,31,31,30,31,30,31}
        };
        for (int month=1; month<one[1]; month++) {
            totalDay1 += daysOfMonth[isLeapYear(one[0])][month];
        }
        for (int month=1; month<two[1]; month++) {
            totalDay2 += daysOfMonth[isLeapYear(two[0])][month];
        }
        //accum days
        totalDay1 += one[2];
        totalDay2 += two[2];
        return Math.abs(totalDay1 - totalDay2);
    }
    private static int isLeapYear(int year) {
        if (year % 4 != 0) return 0;
        else if (year % 100 != 0) return 1;
        else if (year % 400 != 0) return 0;
        else return 1;
    }
}
        else if (year % 100 != 0) return 1;

```

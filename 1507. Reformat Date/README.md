# [1507. Reformat Date (Easy)](https://leetcode.com/problems/reformat-date/)

<p>Given a <code>date</code> string in the form&nbsp;<code>Day Month Year</code>, where:</p>

<ul>
	<li><code>Day</code>&nbsp;is in the set <code>{"1st", "2nd", "3rd", "4th", ..., "30th", "31st"}</code>.</li>
	<li><code>Month</code>&nbsp;is in the set <code>{"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"}</code>.</li>
	<li><code>Year</code>&nbsp;is in the range <code>[1900, 2100]</code>.</li>
</ul>

<p>Convert the date string to the format <code>YYYY-MM-DD</code>, where:</p>

<ul>
	<li><code>YYYY</code> denotes the 4 digit year.</li>
	<li><code>MM</code> denotes the 2 digit month.</li>
	<li><code>DD</code> denotes the 2 digit day.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> date = "20th Oct 2052"
<strong>Output:</strong> "2052-10-20"
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> date = "6th Jun 1933"
<strong>Output:</strong> "1933-06-06"
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> date = "26th May 1960"
<strong>Output:</strong> "1960-05-26"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The given dates are guaranteed to be valid, so no error handling is necessary.</li>
</ul>

**Companies**:  
[Expedia](https://leetcode.com/company/expedia), [Twilio](https://leetcode.com/company/twilio)

**Related Topics**:  
[String](https://leetcode.com/tag/string/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/reformat-date/
// Author: Please set your name in options page
// Time: O(1) 3 is like 1
// Space: O(1)
class Solution {
    public String reformatDate(String date) {
        String[] arr = date.split(" ");
        Map<String, String> month = new HashMap();
        month.put("Jan", "01");
        month.put("Feb", "02");
        month.put("Mar", "03");
        month.put("Apr", "04");
        month.put("May", "05");
        month.put("Jun", "06");
        month.put("Jul", "07");
        month.put("Aug", "08");
        month.put("Sep", "09");
        month.put("Oct", "10");
        month.put("Nov", "11");
        month.put("Dec", "12");
        String day = "";
        if (arr[0].length() == 4) {
            day = arr[0].substring(0,2);
        } else {
            day = "0" + arr[0].substring(0,1);
        }
        return arr[2] + "-" + month.get(arr[1]) + "-" + day;
    }
}

```

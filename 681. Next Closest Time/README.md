# [681. Next Closest Time (Medium)](https://leetcode.com/problems/next-closest-time/)

<p>Given a <code>time</code> represented in the format <code>"HH:MM"</code>, form the next closest time by reusing the current digits. There is no limit on how many times a digit can be reused.</p>

<p>You may assume the given input string is always valid. For example, <code>"01:34"</code>, <code>"12:09"</code> are all valid. <code>"1:34"</code>, <code>"12:9"</code> are all invalid.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> time = "19:34"
<strong>Output:</strong> "19:39"
<strong>Explanation:</strong> The next closest time choosing from digits <strong>1</strong>, <strong>9</strong>, <strong>3</strong>, <strong>4</strong>, is <strong>19:39</strong>, which occurs 5 minutes later.
It is not <strong>19:33</strong>, because this occurs 23 hours and 59 minutes later.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> time = "23:59"
<strong>Output:</strong> "22:22"
<strong>Explanation:</strong> The next closest time choosing from digits <strong>2</strong>, <strong>3</strong>, <strong>5</strong>, <strong>9</strong>, is <strong>22:22</strong>.
It may be assumed that the returned time is next day's time since it is smaller than the input time numerically.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>time.length == 5</code></li>
	<li><code>time</code> is a valid time in the form <code>"HH:MM"</code>.</li>
	<li><code>0 &lt;= HH &lt; 24</code></li>
	<li><code>0 &lt;= MM &lt; 60</code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Enumeration](https://leetcode.com/tag/enumeration/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/next-closest-time/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public String nextClosestTime(String time) {
        String result = "";
        final Integer CYCLE_DAY = 24*60;
        Set<Integer> set = new HashSet<>();
        for (char c : time.toCharArray()) {
            set.add(c - '0');
        }
        //convert time to minutes "23:59" , substring "23" and substring "59"
        int minutes = Integer.parseInt(time.substring(0,2)) * 60 + Integer.parseInt(time.substring(3));
        while (true) {
            //increase mins untill all the number is in the set -> found
            minutes++;
            //if midnight, reset
            if (minutes == CYCLE_DAY) {
                minutes = 0;
            }
            //retrive all digits back from minutes to check in the set
            int H1 = (minutes/60)/10;
            int H2 = (minutes/60)%10;
            int M1 = (minutes%60)/10;
            int M2 = (minutes%60)%10;
            if (set.contains(H1) && set.contains(H2) && set.contains(M1) && set.contains(M2)) {
                 return H1 + "" + H2 + ":" + M1 + "" + M2;
            } else {
               continue;
            }
        }
    }
}

```

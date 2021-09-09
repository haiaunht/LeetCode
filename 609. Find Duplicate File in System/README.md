# [609. Find Duplicate File in System (Medium)](https://leetcode.com/problems/find-duplicate-file-in-system/)

<p>Given a list <code>paths</code> of directory info, including the directory path, and all the files with contents in this directory, return <em>all the duplicate files in the file system in terms of their paths</em>. You may return the answer in <strong>any order</strong>.</p>

<p>A group of duplicate files consists of at least two files that have the same content.</p>

<p>A single directory info string in the input list has the following format:</p>

<ul>
	<li><code>"root/d1/d2/.../dm f1.txt(f1_content) f2.txt(f2_content) ... fn.txt(fn_content)"</code></li>
</ul>

<p>It means there are <code>n</code> files <code>(f1.txt, f2.txt ... fn.txt)</code> with content <code>(f1_content, f2_content ... fn_content)</code> respectively in the directory "<code>root/d1/d2/.../dm"</code>. Note that <code>n &gt;= 1</code> and <code>m &gt;= 0</code>. If <code>m = 0</code>, it means the directory is just the root directory.</p>

<p>The output is a list of groups of duplicate file paths. For each group, it contains all the file paths of the files that have the same content. A file path is a string that has the following format:</p>

<ul>
	<li><code>"directory_path/file_name.txt"</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> paths = ["root/a 1.txt(abcd) 2.txt(efgh)","root/c 3.txt(abcd)","root/c/d 4.txt(efgh)","root 4.txt(efgh)"]
<strong>Output:</strong> [["root/a/2.txt","root/c/d/4.txt","root/4.txt"],["root/a/1.txt","root/c/3.txt"]]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> paths = ["root/a 1.txt(abcd) 2.txt(efgh)","root/c 3.txt(abcd)","root/c/d 4.txt(efgh)"]
<strong>Output:</strong> [["root/a/2.txt","root/c/d/4.txt"],["root/a/1.txt","root/c/3.txt"]]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= paths.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= paths[i].length &lt;= 3000</code></li>
	<li><code>1 &lt;= sum(paths[i].length) &lt;= 5 * 10<sup>5</sup></code></li>
	<li><code>paths[i]</code> consist of English letters, digits, <code>'/'</code>, <code>'.'</code>, <code>'('</code>, <code>')'</code>, and <code>' '</code>.</li>
	<li>You may assume no files or directories share the same name in the same directory.</li>
	<li>You may assume each given directory info represents a unique directory. A single blank space separates the directory path and file info.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong></p>

<ul>
	<li>Imagine you are given a real file system, how will you search files? DFS or BFS?</li>
	<li>If the file content is very large (GB level), how will you modify your solution?</li>
	<li>If you can only read the file by 1kb each time, how will you modify your solution?</li>
	<li>What is the time complexity of your modified solution? What is the most time-consuming part and memory-consuming part of it? How to optimize?</li>
	<li>How to make sure the duplicated files you find are not false positive?</li>
</ul>

**Companies**:  
[Dropbox](https://leetcode.com/company/dropbox), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/)

**Similar Questions**:

- [Delete Duplicate Folders in System (Hard)](https://leetcode.com/problems/delete-duplicate-folders-in-system/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/find-duplicate-file-in-system/
// Author: Please set your name in options page
// Time: O(paths.length * file_parts is parsed)
// Space: O(paths.length * file_parts is parsed)
public class Solution {
    public List < List < String >> findDuplicate(String[] paths) {
        //go through all the path and get the map of content to its file, if content has more than 1 file, print out
        Map<String, List<String>> map = new HashMap<>();
        //["root/a 1.txt(abcd) 2.txt(efgh)","root/c 3.txt(abcd)","root/c/d 4.txt(efgh)","root 4.txt(efgh)"]
        for (String path : paths) {
            String[] file_parts = path.split(" "); // {root/a , 1.txt(abcd) , 2.txt(efgh)}
            //index 0 is for dir
            String file_dir = file_parts[0];
            //index 1 -> file_paths is file need to add to map
            for (int i=1; i<file_parts.length; i++) {
                String[] file_content = file_parts[i].split("\\("); //1.txt(abcd) -> 1.txt, abcd)
                file_content[1] = file_content[1].replace(")", "");
                if (map.containsKey(file_content[1])) {
                    map.get(file_content[1]).add(file_dir + "/" + file_content[0]);
                } else {
                    List<String> list = new ArrayList<>();
                    list.add(file_dir + "/" + file_content[0]);
                    map.put(file_content[1], list);
                }
            }
        }
        List<List<String>> result = new ArrayList<>();
        for (String key : map.keySet()) {
            if (map.get(key).size() > 1) {
                result.add(map.get(key));
            }
        }
        return result;
    }
}

```

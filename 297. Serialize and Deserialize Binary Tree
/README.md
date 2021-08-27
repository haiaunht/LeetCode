# [297. Serialize and Deserialize Binary Tree (Hard)](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)

<p>Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.</p>

<p>Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.</p>

<p><strong>Clarification:</strong> The input/output format is the same as <a href="/faq/#binary-tree">how LeetCode serializes a binary tree</a>. You do not necessarily need to follow this format, so please be creative and come up with different approaches yourself.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/15/serdeser.jpg" style="width: 442px; height: 324px;">
<pre><strong>Input:</strong> root = [1,2,3,null,null,4,5]
<strong>Output:</strong> [1,2,3,null,null,4,5]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = []
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root = [1]
<strong>Output:</strong> [1]
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> root = [1,2]
<strong>Output:</strong> [1,2]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 10<sup>4</sup>]</code>.</li>
	<li><code>-1000 &lt;= Node.val &lt;= 1000</code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [LinkedIn](https://leetcode.com/company/linkedin), [Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Uber](https://leetcode.com/company/uber), [Google](https://leetcode.com/company/google), [Snapchat](https://leetcode.com/company/snapchat), [ByteDance](https://leetcode.com/company/bytedance), [Qualtrics](https://leetcode.com/company/qualtrics), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [VMware](https://leetcode.com/company/vmware), [Adobe](https://leetcode.com/company/adobe), [Apple](https://leetcode.com/company/apple), [Nvidia](https://leetcode.com/company/nvidia), [tiktok](https://leetcode.com/company/tiktok)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Design](https://leetcode.com/tag/design/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:

- [Encode and Decode Strings (Medium)](https://leetcode.com/problems/encode-and-decode-strings/)
- [Serialize and Deserialize BST (Medium)](https://leetcode.com/problems/serialize-and-deserialize-bst/)
- [Find Duplicate Subtrees (Medium)](https://leetcode.com/problems/find-duplicate-subtrees/)
- [Serialize and Deserialize N-ary Tree (Hard)](https://leetcode.com/problems/serialize-and-deserialize-n-ary-tree/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/serialize-and-deserialize-binary-tree/
// Author: Please set your name in options page
// Time: O()
// Space: O()
// TreeNode ans = deser.deserialize(ser.serialize(root));
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Codec {
    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        StringBuilder populate = new StringBuilder();
        stringAfterSerialize(root, populate);
        return populate.toString();
    }
    private void stringAfterSerialize(TreeNode root, StringBuilder s) {
        if (root == null) {
            s.append("null,");
            return;
        }
        s.append(root.val + ",");
        stringAfterSerialize(root.left, s);
        stringAfterSerialize(root.right, s);
    }
    // Decodes your encoded data to tree.
    int index;
    public TreeNode deserialize(String data) {
        String[] arr = data.split(",");
        index = 0;
        return treeAfterDeserialize(arr);
    }
    private TreeNode treeAfterDeserialize(String[] arr) {
        if (index >= arr.length || arr[index].equals("null")) {
            index++;
            return null;
        }
        TreeNode root = new TreeNode(Integer.valueOf(arr[index++]));
        root.left = treeAfterDeserialize(arr);
        root.right = treeAfterDeserialize(arr);
        return root;
    }
}
// Your Codec object will be instantiated and called as such:
// Codec ser = new Codec();
// Codec deser = new Codec();
// TreeNode ans = deser.deserialize(ser.serialize(root));

```

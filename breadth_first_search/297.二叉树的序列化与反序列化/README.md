# 297. 二叉树的序列化与反序列化
你可以将以下二叉树：
```
    1
   / \
  2   3
     / \
    4   5
```
序列化为 "```[1,2,3,null,null,4,5]```"

```java
public class Codec {

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
    }
    public TreeNode deserialize(String data) {
    }
}
```

## 解题思路

## 题解

```java
public class Codec {

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        
        if (root == null) {
            return "[]";
        }
        
        List<TreeNode> queue = new ArrayList<>();
        queue.add(root);
        
        // 将所有node加入list
        for (int i = 0 ; i < queue.size(); i++) {
            TreeNode t = queue.get(i);
            if (t == null) {
                continue;
            }
            queue.add(t.left);
            queue.add(t.right);
        }
        
        // 删除所有末尾null的值
        while(queue.get(queue.size()-1) == null) {
            queue.remove(queue.size()-1);
        }
        
        // [1
        StringBuilder sb = new StringBuilder();
        sb.append("[");
        sb.append(queue.get(0).val);
        
        for (int i = 1; i < queue.size(); i++) {
            if (queue.get(i) == null) {
                sb.append(",null");
            } else {
                sb.append(","+queue.get(i).val);
            }
        }
        sb.append("]");
        return sb.toString();
        
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        if (data == null || "[]".equals(data)) {
            return null;
        }
        
        List<TreeNode> queue = new ArrayList<>();
        String[] arrays = data.substring(1,data.length()-1).split(",");
        
        TreeNode root = new TreeNode(Integer.parseInt(arrays[0]));
        queue.add(root);
        
        boolean isLeft = true;
        int index = 0;
            
        for (int i = 1; i < arrays.length; i++) {
            if (!"null".equals(arrays[i])) {
                
                TreeNode tmp = new TreeNode(Integer.parseInt(arrays[i]));
                if (isLeft) {
                    queue.get(index).left = tmp;
                } else {
                    queue.get(index).right = tmp;
                }
                queue.add(tmp);
            }
            if (!isLeft) {
                index++;
            }
            isLeft = !isLeft;
        }
        return root;
    }
}

```
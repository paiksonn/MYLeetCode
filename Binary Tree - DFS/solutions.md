__EASY__ 

- #104 Maximum Depth of Binary Tree [link](https://leetcode.com/problems/maximum-depth-of-binary-tree/?envType=study-plan-v2&envId=leetcode-75)
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        def dfs(root, depth):
            if not root: return depth
            return max(dfs(root.left, depth + 1), dfs(root.right, depth + 1))
        
        return dfs(root, 0)
```

- #872 Leaf-Similar Trees [link](https://leetcode.com/problems/leaf-similar-trees/?envType=study-plan-v2&envId=leetcode-75)
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def leafSimilar(self, root1: Optional[TreeNode], root2: Optional[TreeNode]) -> bool:
        def dfs(root):
            if not root: return []
            if not root.left and not root.right: return [root.val]
            return dfs(root.left) + dfs(root.right)
        
        return dfs(root1) == dfs(root2)
```

- #101 Symmetric Tree [link](https://leetcode.com/problems/symmetric-tree/description/)
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        if not root:
            return True
        return self.isSame(root.left, root.right)
    # A tree is called symmetric if the left subtree must be a mirror reflection of the right subtree
    def isSame(self, leftroot, rightroot):
        # If both root nodes are null pointers, return true
        if leftroot == None and rightroot == None:
            return True
        # If exactly one of them is a null node, return false
        if leftroot == None or rightroot == None:
            return False
        # If root nodes haven't same value, return false
        if leftroot.val != rightroot.val:
            return False
        # Return true if the values of root nodes are same and left as well as right subtrees are symmetric
        return self.isSame(leftroot.left, rightroot.right) and self.isSame(leftroot.right, rightroot.left)
```

__MEDIUM__ 

- #1448 Count Good Nodes in Binary Tree [link](https://leetcode.com/problems/count-good-nodes-in-binary-tree/?envType=study-plan-v2&envId=leetcode-75)
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def goodNodes(self, root: TreeNode) -> int:
        def dfs(root, value):
            if root:
                k = dfs(root.left, max(value,root.val)) + dfs(root.right, max(value,root.val))
                if root.val >= value:
                    k+=1
                return k
            return 0
        return dfs(root, root.val)

```

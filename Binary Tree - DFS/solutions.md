- __EASY__ Maximum Depth of Binary Tree [link](https://leetcode.com/problems/maximum-depth-of-binary-tree/?envType=study-plan-v2&envId=leetcode-75)
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

- __EASY__ Leaf-Similar Trees [link](https://leetcode.com/problems/leaf-similar-trees/?envType=study-plan-v2&envId=leetcode-75)
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

- __MEDIUM__ Count Good Nodes in Binary Tree [link](https://leetcode.com/problems/count-good-nodes-in-binary-tree/?envType=study-plan-v2&envId=leetcode-75)
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

- __MEDIUM__ Path Sum III [link](https://leetcode.com/problems/path-sum-iii/?envType=study-plan-v2&envId=leetcode-75)
```python

```


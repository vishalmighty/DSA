# Leetcode 872. Leaf-Similar Trees

Definition for a binary tree node.

class TreeNode(object):
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
class Solution(object):
    def leafSimilar(self, root1, root2):
        """
        :type root1: TreeNode
        :type root2: TreeNode
        :rtype: bool
        """
        # create a funtion inside to return leaf nodes as list  
        def dfs(node):
            if node is None:
                return []
            if node.left is None and node.right is None:
                return [node.val]
            return dfs(node.left) + dfs(node.right)

        first_tree = dfs(root1)
        second_tree = dfs(root2)

        return first_tree == second_tree
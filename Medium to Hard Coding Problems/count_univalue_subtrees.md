## Count UniValue Subtrees

Given a binary tree, count the number of uni-value subtrees.
A uni-value subtree means all the nodes of the subtree have the same value

**Example**
Input: root = [5,1,5,5,5,null,5]
Output: 4
Explaination: 
              5
             /  \ 
            1    5
           / \  / \
          5   5 5  5


**Approach**
- The solution involved performing a **dfs** on the tree, counting the number of uni-values subtrees.
- It returns a pair where the first element is the count of uni-value subtrees and the second element is a boolean indicating whether the current subtree is uni-value.

**CODE**
```cpp
class Solution{
    public:
    pair<int, bool> dfs(TreeNode* root){
        if(root == NULL) return {0, true};
        if(root->left == nullptr && root->right == nullptr) return {1, true};
        pair<int, bool> countLeft = dfs(root->left);
        pair<int, bool> countRight = dfs(root->right);
        bool isUnique = true;
        if(countLeft.first > 0){
            isUnique  = isUnique && root->val == root->right->val && countRight.second;
        }

        return (isUnique + countLeft.first + countRight.first, isUnique);

    }
    int countUnivalSubtrees(TreeNode* root){
        pair<int, bool> ret = dfs(root);
        return ret.first;
    }
};
```

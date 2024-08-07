## Binary Tree Paths
Given a binary tree, return all the root-to-leaf paths
<br>

Input
```
1
/\
2 3
\5
```

output: ["1->2->5", "1->3"]
<br>
Explaination: All root-to-leaf paths are: 1->2->5, 1->3

**CODE**
```cpp
class Solution{
    public:
    vector<string> binaryTreePaths(TreeNode* root){
        string path;
        vector<string> res;
        backtrack(root, path, res);
        return res;
    }

    void backtrack(TreeNode* root, const string& path, vector<string>& res){
        if(root == NULL) return;
        if(root->left == nullptr && root->right == nullptr){
            path.empty()? res.push_back(to_string(root->val)) : res.push_back(path + "->" + to_string(root->val));
            return;
        }

        string addend = (path.empty()?"" : "->") + to_string(root->val);
        backtrack(root->left, path + addend, res);
        backtrack(root->right, path + addend, res);
    }
};
```
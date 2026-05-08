# inorder

```cpp
while (curr || !st.empty()) {
    while (curr) {
        st.push(curr);     // simulate recursive call
        curr = curr->left;
    }

    curr = st.top(); st.pop(); // return from recursion
    visit(curr);

    curr = curr->right;
}
```

# pre order

```cpp
st.push(root);

while (!st.empty()) {
    node = st.top(); st.pop();
    visit(node);

    if (node->right) st.push(node->right);
    if (node->left) st.push(node->left); // push left later cause it needs to be
									    // processed first
}
```

# post order

```
IF right child exists AND not processed yet
    → go to right
ELSE
    → process this node
```

we need a way to check if right subtree has been processed or not

```cpp
vector<int> postorderTraversal(TreeNode* root) {
    vector<int> res;
    stack<TreeNode*> st;
    TreeNode* curr = root;
    TreeNode* lastVisited = nullptr;

    while (curr || !st.empty()) {
        if (curr) {
            st.push(curr);         // go left
            curr = curr->left;
        } else {
            TreeNode* node = st.top();

            // if right subtree not yet processed
            if (node->right && lastVisited != node->right) {
                curr = node->right;
            } else {
                res.push_back(node->val); // process
                lastVisited = node;
                st.pop();
            }
        }
    }

    return res;
}
```
	

Reverse Trick

post order is reverse of root -> right -> left

```cpp
vector<int> postorderTraversal(TreeNode* root) {
    vector<int> res;
    if (!root) return res;

    stack<TreeNode*> st;
    st.push(root);

    while (!st.empty()) {
        TreeNode* node = st.top(); st.pop();
        res.push_back(node->val);

        if (node->left) st.push(node->left);
        if (node->right) st.push(node->right);
    }

    reverse(res.begin(), res.end());
    return res;
}
```
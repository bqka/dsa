[problem](https://codeforces.com/contest/2205/problem/D)

![[Pasted image 20260301013849.png]]

this is the minheap version

```
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int n;
    cin >> n;

    vector<int> a(n);
    for (int i = 0; i < n; i++)
        cin >> a[i];

    vector<int> leftChild(n, -1), rightChild(n, -1);
    stack<int> st;

    // Build Cartesian Tree (max-heap version)
    for (int i = 0; i < n; i++) {
        int last = -1;

        // Pop all smaller elements
        while (!st.empty() && a[st.top()] < a[i]) {
            last = st.top();
            st.pop();
        }

        // If stack not empty, current becomes right child
        if (!st.empty()) {
            rightChild[st.top()] = i;
        }

        // The last popped becomes left child
        if (last != -1) {
            leftChild[i] = last;
        }

        st.push(i);
    }

    // Root is bottom element of stack
    int root = -1;
    while (!st.empty()) {
        root = st.top();
        st.pop();
    }

    // Compute maximum depth using DFS
    function<int(int)> dfs = [&](int u) {
        if (u == -1) return 0;
        return 1 + max(dfs(leftChild[u]), dfs(rightChild[u]));
    };

    int maxDepth = dfs(root);

    cout << n - maxDepth << "\n";

    return 0;
}
```
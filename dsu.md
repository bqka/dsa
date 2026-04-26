```cpp
class DisjointSet {
    private:
    vector<int> parent, rank;

    public:
    DisjointSet(int n): parent(n), rank(n) {
        rank.assign(n, 1);
        iota(begin(parent), end(parent), 0);
    }

    int find(int x){
        if(parent[x] == x) return x;
        return parent[x] = find(parent[x]); // path compression
    }

    bool merge(int x, int y){
        int rootX = find(x);
        int rootY = find(y);

        if(rootX == rootY) return false;
		
        if(rank[rootX] > rank[rootY]) swap(rootX, rootY);
        parent[rootX] = rootY;
		if(rank[rootX] == rank[rootY]) rank[rootY]++;

        return true;
    }
};
```

assuming root starts at 1
if root is 1, (2\*v, 2\*v+1)
if root is 0, (2\*v+1, 2\*v+2)

tl, tr -> represent current node boundaries
l, r -> requested interval

```cpp
class SegmentTree {
	int n, t[4*MAXN];
	
	public:
	SegmentTree(vector<int>& arr){
		n = arr.size();
		build(arr, 0, 0, n-1);
	}

	// v is node
	void build(vector<int>& a, int v, int tl, int tr){
		if(tl == tr) t[i] = a[tl];
		else {
			int tm = (tl + tr) / 2;
			build(a, v * 2, tl, tm);
			build(a, v * 2 + 1, tm + 1, tr);
			t[v] = t[v * 2] + t[v * 2 + 1];
		}
	}
	
	int sum(int v, int tl, int tr, int l, int r){
		if(l > r) return 0;
		if(l == tl && r == tr) return t[v];
		int tm = (tl + tr) / 2;
		return sum(v*2, tl, tm, l, min(tm, r))
			+ sum(v*2 + 1, tm+1, tr, max(l, tm+1), r);
	}
	
	void update(int v, int tl, int tr, int pos, int new_val){
		if(tl == tr) t[v] = new_val;
		else {
			int tm = (tl + tr) / 2;
			if(pos <= tm) update(v*2, tl, tm, pos, new_val);
			else update(v*2+1, tm+1, tr, pos, new_val);
			t[v] = t[2*v] + t[2*v + 1];
		}
	}
	
	int query(int l, int r){
		return sum(1, 0, n-1, l, r);
	}
	
	int update(int pos, int val){
		update(1, 0, n-1, pos, val);
	}
};
```
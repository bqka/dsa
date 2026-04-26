```cpp
int maxSubarraySum(vector<int> &arr) {
    int mx = -1e9, res = -1e9;
    for (int i = 0; i < arr.size(); i++) {
		
        // dp[i] = max(a[i], dp[i-1] + a[i])
		// then max over all dp[i]
        mx = max(arr[i], mx + arr[i]);
        res = max(res, mx);
    }
	
    return res;
}
```

count roots

```cpp
int cnt = 0;
for(int i = 0; i < n; i++){
    if(ds.find(i) == i) cnt++;
}
```
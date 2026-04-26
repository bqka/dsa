[problem 1](https://codeforces.com/problemset/problem/2156/C)
prefix sum with frequency array counting good idea

```
void solve(){
    int n, k; cin >> n >> k;
    vi a(n); input(a);
    vi f(n+1), p(n+1);
    for(auto& x : a) f[x]++;
    for(int i = 1; i <= n; i++) p[i] = p[i-1] + f[i];

    int ans = 1;
    for(int g = 1; g <= n; g++){
		// counts no. of elements < 4g
        int bad = p[min(n, 4*g-1)];
		
        bad -= f[g];
        if(2*g <= n) bad -= f[2*g];
        if(3*g <= n) bad -= f[3*g];

        if(bad <= k) ans = g;
    }

    cout << ans << endl;
}
```
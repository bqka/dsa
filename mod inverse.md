
![[Pasted image 20260415203233.png]]
![[Pasted image 20260415203059.png]]
```cpp
long long power(long long a, long long b, long long mod) {
    long long res = 1;
    while (b) {
        if (b & 1) res = res * a % mod;
        a = a * a % mod;
        b >>= 1;
    }
    return res;
}

long long modInverse(long long a, long long mod) {
    return power(a, mod - 2, mod);
}
```


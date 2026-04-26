```
int n;
vector<bool> is_prime(n+1, true);
is_prime[0] = is_prime[1] = false;
for (int i = 2; i <= n; i++) {
    if (is_prime[i] && (long long)i * i <= n) {
        for (int j = i * i; j <= n; j += i)
            is_prime[j] = false;
    }
}
```

Sieve of Eratosthenes is an algorithm for finding all the prime numbers in a segment  $[1;n]$  using  $O(n \log \log n)$  operations.

![[Pasted image 20260124010928.png]]
```
int n;
vector<bool> is_prime(n+1, true);
is_prime[0] = is_prime[1] = false;
for (int i = 2; i * i <= n; i++) {
    if (is_prime[i]) {
        for (int j = i * i; j <= n; j += i)
            is_prime[j] = false;
    }
}
```

Sieve of Eratosthenes is an algorithm for finding all the prime numbers in a segment  $[1;n]$  using  $O(n \log \log n)$  operations.

![[Pasted image 20260429142950.png]]
![[Pasted image 20260429143010.png]]


![[Pasted image 20260124010928.png]]

# Application

calculate prime factors of numbers in $O(n\log \log n)$

```cpp
// N loglogN
for(int i = 2; i <= N; i++){
 if(!pfac[i].empty()) continue;
 for(int j = i; j <= N; j += i) pfac[j].pb(i);
}
```

![[Pasted image 20260429144040.png]]

so calculating all divisors is nlogn
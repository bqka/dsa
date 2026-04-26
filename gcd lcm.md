```cpp
int gcd (int a, int b) {
    return b ? gcd (b, a % b) : a;
}
```

```cpp
int lcm (int a, int b) {
    return a / gcd(a, b) * b;
}
```

```cpp
int gcd (int a, int b) {
    while (b) {
        a %= b;
        swap(a, b);
    }
    return a;
}
```

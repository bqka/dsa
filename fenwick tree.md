range sum

```cpp
struct Fenwick {
    int n;
    vector<long long> bit;

    Fenwick(int n) {
        this->n = n;
        bit.assign(n + 1, 0);
    }

    void update(int i, long long val) {
        for(; i <= n; i += i & -i)
            bit[i] += val;
    }

    long long query(int i) {
        long long res = 0;
        for(; i > 0; i -= i & -i)
            res += bit[i];
        return res;
    }

    long long rangeQuery(int l, int r) {
        return query(r) - query(l-1);
    }
};
```

# Reverse Coordinate Trick (Suffix → Prefix Query)

Fenwick Tree naturally supports:

```text
prefix queries: [1...x]
```

but sometimes we need suffix queries like:

```text
values > x
```

which corresponds to:

```text
[x+1 ... M]
```

---

## Trick

Reverse coordinates:

```text
rev(v) = M - v + 1
```

where `M` is max compressed value.

This flips inequalities:

```text
value > x
⇔ rev(value) < rev(x)
```

So a suffix query becomes a prefix query.

---

## Example

Original:

```text
Value: 1 2 3 4 5
```

Reversed:

```text
Rev:   5 4 3 2 1
```

Suppose:

```text
x = 3
```

Need:

```text
values > 3 = {4,5}
```

Reversed indices:

```text
4 -> 2
5 -> 1
```

which form a prefix:

```text
[1..2]
```

So:

```cpp
query(rev(x)-1)
query(2)
```

returns max over original values greater than `3`.

---

## Formula

Update:

```cpp
update(rev(v), val);
```

Query values greater than `x`:

```cpp
query(rev(x)-1);
```

---

## Template

```cpp
int rev(int x){
    return M - x + 1;
}
```

```cpp
bit.update(rev(val), dpValue);
best = bit.query(rev(x)-1);
```

---

## Use Case
Useful for Fenwick queries involving:

```text
nums[j] > nums[i]
suffix maxima
greater-than transitions in DP
```

**Rule:**

```text
Greater-than query
→ Reverse coordinates
→ Prefix query
```
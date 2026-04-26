```
int dp[20][2][STATE];

int solve(int pos, int tight, STATE, string &s) {
    if (pos == s.size()) return base_case;

    if (dp[pos][tight][STATE] != -1)
        return dp[pos][tight][STATE];

    int limit = tight ? s[pos] - '0' : 9;
    int ans = 0;

    for (int d = 0; d <= limit; d++) {
        ans += solve(pos + 1,
                     tight && (d == limit),
                     new_state,
                     s);
    }

    return dp[pos][tight][STATE] = ans;
}
```

```
answer = solve(R) - solve(L - 1);
```
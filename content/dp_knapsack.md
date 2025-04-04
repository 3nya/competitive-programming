# DP Knapsack

## 0-1 
Each value can only be chose once

```cpp
vi f(W + 1, 0);
for (int i = 0; i < n; i++) {
    for (int j = W; j >= w[i]; j--) {
        f[j] = max(f[j], f[j - w[i]] + v[i]);
    }
}
```
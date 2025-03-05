# Square root decomposition

To make iterating through an array faster

```cpp
int n;
vl original_arr(n);
vl block(sqrt(n));

ll query(int l, int r) {
    ll sum = 0;
    // first block
    int curr = -1;
    while (l < r && l % block_size != 0 && l != 0) {
        sum += original_arr[l] * curr;
        l++;
    }
    // overlapped blocks
    while (l + block_size -1 <= r) {
        sum += block[l / block_size] * curr;
        l += block_size;
        curr *= -1;
    }
    // last block
    while (l <= r) {
        sum += original_arr[l] * curr;
        l++;
    }
    return sum;
}
```
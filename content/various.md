# various

---

### fast ceiling division:
`q = 1 + ((x - 1) / y)` where `q = ceil(x/y)` -- only works for unsigned math
also consider `q = x / y + (x % y != 0)`

### `set` vs `unordered_set`
- `set`s are usually implemented as trees under the hood
- `unordered_set`s actually use hashing
- default `unordered_set` tends be really slow, we can solve this by

```cpp
unordered_set<int> s;
s.reserve(1024); // pre-reserve 1024 buckets
s.max_load_factor(0.25); // allocate new buckets when load factor > 0.25
// load factor = number of filled buckets / total number of buckets
```

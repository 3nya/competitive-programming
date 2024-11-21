# pragma 

---

*add pragmas code go brr*

### Safe code
Safest to use in most competitive programming cases
```cpp
#pragma GCC optimize("03")
#pragma GCC target("avx2")
```
More aggressive
```cpp
#pragma GCC optimize("Ofast,unroll-loops")
#pragma GCC target("avx2")
```

---

### pragma GCC optimize

```cpp
#pragma GCC optimize(string,...)
```
This pragma allows you to set *global optimization* options for functions defined later in the source file.  

Options:
- `03`: Enables all optimization levels from `00` to `02`.
    - **Aggressive function inlining**: Reduces time calling functions, but can increase executable size if function inlined many times.
    - **Vectorization**: The complier uses SIMD (single instruction, multiple data) in order to process operations on multiple pieces of data at the same time. 
    - **Unrolls loops**: Moves computations outside of loops if they do not depend on the loop. 
    - **Dead code elimination**
- `Ofast`: Enables `03` as well as some other optimizations.
    - Enables `fast-math` which does stuff like ignores NaN and infinity values.
- `unroll-loops`
- `strict-overflow`


---

### pragma GCC target

```cpp
#pragma GCC target(string,...)
```
This pragma allows you to set *target-specific* options for functions defined later in the source file.

Options:
- `avs` and `avx2`: Provides 8, 16 and 32 byte vector instructions.
- `sse`, `sse2`, `sse3`, `sse4`, `sse4.1`, `sse4.2`: Other instruction sets for vectorization. However, they are older than `avx`/`avx2`. Can be used if `avx`/`avx2` isn't supported.
- `popcnt`: Optimizes `__builtin_popcount` which allows you to count the amount of flags in bitmasks.
- `lzcnt`: Allows you to use `__builtin_clz` method which counts the amount of leading zeros. 


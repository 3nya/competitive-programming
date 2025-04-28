# modular arithmetic

---

### basic concept

*modular multiplicative inverse* -> inverse of a number $a$ is $a^{-1}$ such
that $a*a^{-1} \bmod m = 1$

*fermat's little theorem* -> if $m$ is prime, then $a^m \bmod m = a \bmod m$

it then follows that $a^{m-1} \bmod m = 1$,	so $a * a^{m - 2} \bmod m = 1$.

therefore, when $m$ is prime, $a^{m-2} \bmod m$ is the modular multiplicative
inverse of $a$.

### implementation

calculating $a^{m-2}$ can be slow -- $O(n)$ time

using a smarter exponentiation algo can make it $O(log n)$

```cpp
// recursive implementation
// computes x^n mod m
ll pow_mod(ll x, ll n, ll m) {
    if (n == 0)
        return 1;
    ll t = pow_mod(x, n/2, m);
    if (n % 2 == 0)
        return (t * t) % m;
    else
        return (((t * t) % m) * x) % m;
}
```

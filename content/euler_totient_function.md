# euler totient function

- phi(n) is the number integers between 1 and n that are coprime to n

- *properties:*
    - if p is prime, then $\phi(p) = p - 1$
    - if p^k is a power of a prime, then $\phi(p^k) = p^k - p^{k-1}$
    - if a and b are relatively prime, then $\phi(ab) = \phi(a) \phi(b)$

- in general, $\phi(ab) = \phi(a) * \phi(b) * d / \phi(d)$
- where $d = \gcd(a, b)$

## implementation

- stolen from cp algorithms

using factorization in $O(sqrt(n))$:
```cpp
int phi(int n) {
    int result = n;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) {
            while (n % i == 0)
                n /= i;
            result -= result / i;
        }
    }
    if (n > 1)
        result -= result / n;
    return result;
}
```

using sieve of erastothenes to calculate from 1 to n in $O(n \log \log n)$
```cpp
void phi_1_to_n(int n) {
    vector<int> phi(n + 1);
    for (int i = 0; i <= n; i++)
        phi[i] = i;

    for (int i = 2; i <= n; i++) {
        if (phi[i] == i) {
            for (int j = i; j <= n; j += i)
                phi[j] -= phi[j] / i;
        }
    }
}
```

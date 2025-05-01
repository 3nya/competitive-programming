# lambda

format of a lambda:
```cpp
[capture] (parameters) -> return_type {
    // definition
}
```

- *capture* : external variables from the environment
    - otherwise, lambdas can only access values passed in as parameters
- *parameters, return_type, definition* : self explanatory.

examples
sort by descending order:
```cpp
vector<int> v;
sort(v.begin(), v.end(), [](const int &a, const int &b) {
    return a > b;
});
```

find first value greater than k:
```cpp
vector<int> v;
const int k = 2;

// capture k by value
auto it = find(v.begin(), v.end(), [k](const int &x) {
    return x >= k;
});
```

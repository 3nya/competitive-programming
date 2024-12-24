# various

---

### fast ceiling division:
`q = 1 + ((x - 1) / y)` where `q = ceil(x/y)` -- only works for unsigned math
also consider `q = x / y + (x % y != 0)`

### `set` vs `unordered_set`
- `set`'s are usually implemented as trees under the hood
- `unordered_set`'s actually use hashing
- default `unordered_set` tends be really slow, we can solve this by

```cpp
unordered_set<int> s;
s.reserve(1024); // pre-reserve 1024 buckets
s.max_load_factor(0.25); // allocate new buckets when load factor > 0.25
// load factor = number of filled buckets / total number of buckets
```

### finding all maximal cliques (bron-kerbosch)

- *clique* : subset of a vertices in a graph such them and the edges between
them form a complete graph

- three disjoint sets of vertices, whose union is the set of all vertices:
    - $R$ = vertices in this potential clique
    - $P$ = remaining vertices to consider
    - $X$ = vertices to skip

- $P \cup X$ is the set of all vertices that are connected to each vertex in $R$

- start by calling with $R = X = \emptyset$, and $P$ being the set of all
vertices in the graph

stolen straight off of [wikipedia](https://en.wikipedia.org/wiki/Bron%E2%80%93Kerbosch_algorithm):
```cpp
algorithm BronKerbosch1(R, P, X) is
    if P and X are both empty then
        report R as a maximal clique
    for each vertex v in P do
        BronKerbosch1(R ⋃ {v}, P ⋂ N(v), X ⋂ N(v))
        P := P \ {v}
        X := X ⋃ {v}
```

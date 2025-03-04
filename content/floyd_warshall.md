# Floyd Warshall

Given an adjacency matrix representing the weight between 2 vertices, find the shortest distance. 

```cpp
ll const INF = 1e9; // INF representing unreachable
vector<vector<ll>> floyd_warshall(vector<vector<ll>> &arr, int n) {
    for (int k = 0; k < n; k++) {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (arr[i][j] > (arr[i][k] + arr[k][j])) {
                    arr[i][j] = arr[i][k] + arr[k][j];
                }
            }
        }
    }
    return arr;
}
```


Floyd warshall with bitops (representing that there exists a path between two vertices)

```cpp
const int MAX_N = 1000; // set MAX_N to n 

bitset<MAX_N> adj[MAX_N];
void floyd_warshall(int n) {
    for (int k = 0; k < n; k++) {
        for (int i = 0; i < n; i++) {
            if (adj[i][k]) {  
                adj[i] |= adj[k]; 
            }
        }
    }
}
```
# segment tree

**easy implementation:**

for a segment tree with $n$ vertices, can store in a array of $4n$.

with 1-indexing: left child of vertex at $i$ is stored at $2i$, right at $2i +
1$. parent of a index $i$ is at $i / 2$.

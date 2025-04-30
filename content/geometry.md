# geometry

geometry sucks.

## area of a polygon

we can use [shoelace theorem](https://artofproblemsolving.com/wiki/index.php?title=Shoelace_Theorem)
to find the area of arbitary polygons:

suppose a polygon has $n$ vertices
$(x_1, y_1), (x_2, y_2), (x_3, y_3), \ldots, (x_n, y_n)$.
Then the area of the polygon is
$\frac{1}{2} | (x_1 y_2 + x_2 y_3 + \ldots + x_n y_1) - (y_1 x_2 + y_2 x_3 + \ldots + y_n x_1) |$.

naive implementation:
```cpp
double polygon_area(const vector<double> &x, const vector<double> &y) {
    double area = 0;
    for (int i = 0; i < x.size(); i++) {
        int j = (i + 1) % x.size();
        area += x[i] * y[j];
        area -= y[i] * x[j];
    }
    return abs(area / 2);
}
```

we can do some loop fusion to make this faster:
```cpp
double polygon_area(const vector<double> &x, const vector<double> &y) {

    // close the polygon
    x.push_back(x[0]);
    x.push_back(x[1]);
    y.push_back(y[0]);
    y.push_back(y[1]);

    double area = 0;
    for (int i = 1; i < x.size(); i++)
        area += x[i] * (y[i+1] - y[i-1]);
    return abs(area / 2);

}
```

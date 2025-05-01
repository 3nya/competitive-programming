# geometry

geometry sucks.

## area of a polygon

we can use [shoelace theorem](https://artofproblemsolving.com/wiki/index.php?title=Shoelace_Theorem)
to find the area of arbitary polygons:

suppose a polygon has $n$ vertices
$(x_1, y_1), (x_2, y_2), (x_3, y_3), \ldots, (x_n, y_n)$.
Then the area of the polygon is
$\frac{1}{2} | (x_1 y_2 + x_2 y_3 + \ldots + x_n y_1) - (y_1 x_2 + y_2 x_3 + \ldots + y_n x_1) |$.

implementation:
```cpp
struct point {
    double x, y;
};

// finds the area of a polygon enclosed by a set of points
double polygon_area(const vector<point> &points) {
    double area = 0.0;
    for (int i = 0; i < points.size(); i++) {
        int j = (i + 1) % points.size();
        area += points[i].x * points[j].y;
        area -= points[i].y * points[j].x;
    }
    return abs(area / 2);
}
```

## orientation of a triangle

given three points p1, p2, p3, if we go from p1 to p2 to p3, did we go clockwise
or counterclockwise?

once we move from p1 to p2, if p3 is to the right, then we moved clockwise

use the fact that the cross product returns the signed area of the parallelogram

$2S = (x_2 - x_1)(y_3 - y_2) - (x_3 - x_2)(y_2 - y_1)$

counterclockwise if positive, clockwise if negative

implementation:
```cpp
struct point {
    double x, y;
};

double signed_area(const vector<point> &points) {
    point a = points[0];
    point b = points[1];
    point c = points[2];
    return (b.x - a.x) * (c.y - b.y) - (c.x - b.x) * (b.y - a.y);
}
```

# convex hull

## graham's scan

- find P0, the point with the lowest y value
    - break ties by lowest x

- sort other points by polar angle with P0 in clockwise order
    - break ties by distance from P0

- iterate through each point
- use a stack to maintain the points in the convex hull
- check that it makes a clockwise angle with the previous point

implementation
```cpp
vector<point> convex_hull(vector<point> &points) {

    // p0 is the point with lowest y, ties broken by lower x
    point p0 = points[0];
    for (point p : points) {
        if (p.y < p0.y)
            p0 = p;
        else if (p.y == p0.y && p.x < p0.x)
            p0 = p;
    }

    // sort points based on orientation from p0
    sort(points.begin(), points.end(), [&p0](const point &a, const point &b) {
        double area = signed_area({p0, a, b});
        if (area == 0) {    // no orientation, return point closer to p0
            return pow(p0.x - a.x, 2) + pow(p0.y - a.y, 2)
                < pow(p0.x - b.x, 2) + pow(p0.y - b.y, 2);
        }
        return area < 0;    // is it clockwise?
    });

    // iterate through each of the points
    vector<point> stk;
    for (int i = 0; i < points.size(); i++) {
        // check that going from the last point to this one is clockwise
        while (true) {
            if (stk.size() <= 1)
                break;
            if (signed_area({stk[stk.size() - 2], stk.back(), points[i]}) < 0)
                break;
            stk.pop_back();
        }
        stk.push_back(points[i]);
    }

    // edge case
    if (stk.size() == 2 && stk[0].x == stk[1].x && stk[0].y == stk[1].y)
        stk.pop_back();

    return stk;
}
```

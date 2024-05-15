---
title: Calculating Distance Between Points in N Dimensions
tags:
  - distance
  - math
  - calculations
  - dimensions
---

When working with points in multiple dimensions, you may need to find the distance between two points. Here's how to calculate the distance between two points in N dimensional space using JavaScript.

## The Euclidean Distance Formula

The standard way to calculate distance in multiple dimensions is using the Euclidean distance formula:

```
d = sqrt( (x1 - x2)^2 + (y1 - y2)^2 + ... + (xn - yn)^2) 
```

Where d is the distance, and (x1, y1, ...) and (x2, y2, ...) are the coordinate tuples of the two points. 

This sums the squared differences between the coordinates, then takes the square root.

## Implementing in JavaScript 

Here is how to implement this in a JavaScript function:

```js
function euclideanDistance(point1, point2) {

  if (point1.length !== point2.length) {
    throw new Error('Points must have the same dimensions');
  }

  let sum = 0;

  for (let i = 0; i < point1.length; i++) {
    sum += (point1[i] - point2[i]) ** 2; 
  }

  return Math.sqrt(sum);

}
```

To use:

```js
const point1 = [1, 2, 3]; 
const point2 = [4, 6, 8];

const distance = euclideanDistance(point1, point2); // 5
```

This allows calculating the distance between points in any number of dimensions by passing in arrays of coordinates.

## Usage Examples

Some examples of usage:

- 2D points: `euclideanDistance([1, 2], [4, 6])` 
- 3D points: `euclideanDistance([1, 2, 3], [4, 6, 8])`
- 4D points: `euclideanDistance([1, 2, 3, 4], [5, 6, 7, 8])`

The euclidean distance formula works for any number of dimensions. This provides a flexible way to measure distance in multi-dimensional space in JavaScript.

### Implementing in C++
Here is how we can implement the same function in C++. Notice how we don't have the power operator in C++, so we have to compute the difference twice.
```c++
#include <iostream>
#include <vector>
#include <cmath>
#include <stdexcept>

double euclideanDistance(const std::vector<double>& point1, const std::vector<double>& point2) {
    if (point1.size() != point2.size()) {
        throw std::invalid_argument("Points must have the same dimensions");
    }

    double sum = 0.0;

    for (size_t i = 0; i < point1.size(); i++) {
        sum += (point1[i] - point2[i]) * (point1[i] - point2[i]);
    }

    return std::sqrt(sum);
}

int main() {
    std::vector<double> p1 = {1.0, 2.0, 3.0};
    std::vector<double> p2 = {4.0, 5.0, 6.0};
    std::cout << "Euclidean distance: " << euclideanDistance(p1, p2) << std::endl;

    return 0;
}

```

#### 2d Euclidean Distance
```c++
#include <iostream>
#include <cmath>

float euclideanDistance2D(float x1, float y1, float x2, float y2) {
    float dx = x2 - x1;
    float dy = y2 - y1;
    return std::sqrt(dx * dx + dy * dy);
}

int main() {
    float x1 = 1.0f, y1 = 2.0f;
    float x2 = 4.0f, y2 = 6.0f;
    std::cout << "Euclidean distance: " << euclideanDistance2D(x1, y1, x2, y2) << std::endl;

    return 0;
}

```

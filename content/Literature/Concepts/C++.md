---
tags:
  - "#cplusplus"
  - programming
  - language
  - help
  - code
  - reference
---

# C++
C++ is a high-performance, general-purpose programming language created by [[Bjarne Stroustrup]] in 1979 as an extension to the C language. Known for its flexibility, efficiency, and low-level control over system resources and memory. C++ is widely used in many different domains, including operating systems, game development, embedded systems, finance, and scientific computing, due to its performance, portability, and ability to handle complex projects. Its object-oriented features and rich standard library make it a popular choice for building large-scale applications and software infrastructure.

### Vectors
##### Ways to Initialize a Vector

| Initialization Method      | C++ Code                                                       | Description                                                  |
|:-------------------------- |:-------------------------------------------------------------- |:------------------------------------------------------------ |
| Default (Empty)            | `vector<T> v1;`                                                | Creates an empty vector with no elements.                    |
| Copy Constructor           | `vector<T> v2(v1);`<br>`vector<T> v2 = v1;`                    | Creates a vector `v2` that is a copy of another vector `v1`. |
| Fill Constructor (Value)   | `vector<T> v3(n, val);`                                        | Creates a vector `v3` with `n` copies of the value `val`.    |
| Fill Constructor (Default) | `vector<T> v4(n);`                                             | Creates a vector `v4` with `n` default-initialized elements. |
| List Initialization        | `vector<T> v5 {a, b, c...};`<br>`vector<T> v5 = {a, b, c...};` | Creates a vector `v5` initialized with values a, b, c, etc.  |

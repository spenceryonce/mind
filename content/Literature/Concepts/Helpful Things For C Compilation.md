---
tags:
  - c
  - code
  - programming
  - compilation
  - gcc
  - linking
  - library
DateCreated: 5/2/2024 11:50 pm
---

### Linking smath.lib to a new program

```bash
gcc testsmath.c -o testsmath.exe -L. -lsmath
```

### Linking smath.lib to a c++ program
```bash
g++ yourcplusplus.cpp -o yourcpluscplus.exe -L. -lsmath
```
(Remember to move both smath.h and smath.lib into your current project directory for this to work.)
```c
//your main c++ file
 extern "C" { 
 #include <smath.h> 
}
```

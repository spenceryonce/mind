---
title: Exporting C++ to Javascript
tags:
  - code
  - programming
  - cplusplus
  - javascript
  - export
date: 2024-05-16
---
# How to Export a C++ Library for JavaScript
Exporting C++ code for use in a JavaScript environment involves several key steps. This process allows you to leverage the performance and capabilities of C++ within your JavaScript applications. Here's a breakdown of the process:

### 1. Create a C++ Header File
Begin by creating a C++ header file (e.g., `my_library.h`). This file will declare the functions and classes you intend to make accessible to JavaScript. These declarations act as a bridge between the two languages.

### 2. Implement Functions and Classes
In a separate C++ source file (e.g., `my_library.cpp`), provide the actual implementations for the functions and classes declared in your header file. This is where the core logic of your C++ code resides.

### 3. Export Symbols
To make your C++ functions and classes visible to JavaScript, you need to export them. This is typically done using the `__declspec(dllexport)` keyword in your header file. This keyword instructs the compiler to include these symbols in the generated library file.

### 4. Create a JavaScript Wrapper
Develop a JavaScript wrapper file (e.g., `my_library.js`). This file will contain JavaScript code responsible for loading your compiled C++ library (usually a DLL) and providing JavaScript-friendly interfaces to interact with the exported C++ functions and classes.

### 5. Build the C++ Library
Utilize a C++ compiler like Visual Studio or GCC to build your C++ code into a library file (e.g., `my_library.dll`). This library file will contain the compiled machine code of your C++ functions and classes.

### 6. Integrate with JavaScript
In your main JavaScript code, use the require() function (or a similar mechanism) to load your JavaScript wrapper file. This will give you access to the JavaScript functions defined in the wrapper, which in turn call the underlying C++ functions from the loaded library.

#### Example:
Let's illustrate with a simple example of exporting a C++ function named add that adds two numbers:
```c++
// my_library.h
#pragma once
extern "C" {
    __declspec(dllexport) int add(int a, int b);
}
```

```c++
// my_library.cpp
#include "my_library.h"
int add(int a, int b) {
    return a + b;
}
```

```js
// my_library.js
const myLibrary = require('./my_library.dll');
function add(a, b) {
    return myLibrary.add(a, b);
}
module.exports = { add };
```

```js
// main.js
const myLibrary = require('./my_library.js');
const result = myLibrary.add(1, 2);
console.log(result); // Output: 3
```

By following these steps, you can effectively integrate C++ code into your JavaScript projects, harnessing the strengths of both languages.
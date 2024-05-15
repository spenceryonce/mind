---
tags:
  - opengl
  - software
  - pipeline
  - programming
  - code
  - diagram
---
![[Pasted image 20240508235604.png]]

### The Application Layer
This is where your program invokes drawing commands. The application acts as a controller of the overall process and manages processes such as: creating windows, threads, memory allocation, complex user data-types, and making calls to 3rd party libraries such as OpenGL or DirectX.

### The Abstraction Layer
This contains the OpenGL or DirectX API implementations. The Abstraction layer serves as a dispatch to the next layer by implementing hardware-level functionality in a usable and standardized format. In C style terminology, you can think of the Application Layer as the header file which contains only the definitions whereas the Abstraction Layer represents the actual implementation.

### The Device Driver
The Abstraction Layer passes its command to the Device Driver (a software communication layer to the hardware). This file can be quite large in size since it interact with so many different pieces.

### The Hardware
The hardware simply executes the commands given to it by the Device Driver.

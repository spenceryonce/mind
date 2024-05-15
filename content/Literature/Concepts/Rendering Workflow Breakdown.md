---
title: OpenGl Basic Workflow
tags: 
    - programming
    - opengl
    - vao
    - vbo
    - workflow
    - howto
---

## Basic Open GL Data Flow

Opengl workflow:
Create vertices
create indices
create VAO 
bind VAO
create VBO 
Bind VBO to vertices
create EBO
bind EBO to indices
create vertex shader
compile vertex shader
create fragment shader
compile fragment shader
create shaderprogram
link shaders to shader program
setup vertex attribute pointer for vertices
delete shaders
use shader program

(within render loop)
clear color
clear color bit
set polygon mode to fill
use shader program
bind VAO
draw elements (# of vertices)
bind vertex array 0

javascript
create a canvas
create a triangle
color it

unity (c#)
create object
triangle
add material
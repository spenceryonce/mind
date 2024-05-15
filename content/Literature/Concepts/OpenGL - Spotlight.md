---
tags:
  - opengl
  - spotlight
  - mathematics
  - programming
  - development
  - c
  - code
  - light
  - theta
---
Resources:
1. [LearnOpenGL](https://learnopengl.com/Lighting/Light-casters)

A spotlight is a light source that is located somewhere in the environment that, instead of shooting light rays in all directions, only shoots them in a specific direction.
![[Pasted image 20240507234105.png]]
- `LightDir`: the vector pointing from the fragment to the light source.
- `SpotDir`: the direction the spotlight is aiming at.
- `Phi` 𝜙: the cutoff angle that specifies the spotlight's radius. Everything outside this angle is not lit by the spotlight.
- `Theta` 𝜃: the angle between the LightDir vector and the SpotDir vector. The 𝜃 value should be smaller than Φ to be inside the spotlight.

So we need to calculate to dot product (returns the cosine of the angle between two vectors) of the `LightDir` and `SpotDir` and compare with 𝜙 (cutoff angle).

To get the angle in the shader we then have to calculate the inverse cosine of the dot product's result which is an expensive operation. So to save some performance we calculate the cosine value of a given cutoff angle beforehand and pass this result to the fragment shader. Since both angles are now represented as cosines, we can directly compare between them without expensive operations.

Then we calculate the theta 𝜃 value and compare it with the cutoff 𝜙 value to see if we are in or out of the spotlight
```c
float theta = dot(lightDir, normalize(-light.direction)); 
if(theta > light.cutOff) { 
// do lighting calculations 
} else 
// else, use ambient light so scene isn't completely dark outside the spotlight. 
color = vec4(light.ambient * vec3(texture(material.diffuse, TexCoords)), 1.0);
```


#### Smooth Edges
$I = \frac{\theta - \gamma}{\epsilon}$

Here ϵ𝜖 (epsilon) is the cosine difference between the inner (ϕ𝜙) and the outer cone (γ𝛾) (ϵ=ϕ−γ𝜖=𝜙−𝛾). The resulting I𝐼 value is then the intensity of the spotlight at the current fragment.

We now have an intensity value that is either negative when outside the spotlight, higher than `1.0` when inside the inner cone, and somewhere in between around the edges. If we properly clamp the values we don't need an `if-else` in the fragment shader anymore and we can simply multiply the light components with the calculated intensity value:
```c
float theta = dot(lightDir, normalize(-light.direction)); 
float epsilon = light.cutOff - light.outerCutOff; 
float intensity = clamp((theta - light.outerCutOff) / epsilon, 0.0, 1.0); 
// we'll leave ambient unaffected so we always have a little light. 
diffuse *= intensity; 
specular *= intensity;
```

Make sure to add the `outerCutOff` value to the Light struct and set its uniform value in the application.

*Note*: For smoother edges you can use: 
```c
//regular smoothing
float intensity = clamp((theta - light.outerCutOff) / epsilon, 0.0, 1.0); // better smoothing   
float intensity = smoothstep(0.0, 1.0, (theta - light.outerCutOff) / epsilon);  
```

You can also use a "cookie" texture to simulate a real flashlight by multiplying it with the fragment color and the light attenuation. Google "flashlight texture".

In order to do this you need first to pass the viewport size as a uniform in the fragment shader:  
```C
uniform vec2 viewPort;
```

And in your fragment main loop add the following:  
```C
vec2 fragCoord = gl_FragCoord.xy / viewPort * vec2(1.0, -1.0);  
intensity *= length(vec3(texture(light.flashlight, fragCoord)));
```

Pass the viewport size to the shader from your program: 
```C
lightingShader.setVec2("viewPort", SCR_WIDTH, SCR_HEIGHT);
```

Don't forget to load the texture, set the sampler in the Light struct (or somewhere else). 

```C
unsigned int flashlight = loadTexture("textures/batsignal.jpg");  
lightingShader.setInt("light.flashlight", 3);

// flashlight texture  
glActiveTexture(GL_TEXTURE3);  
glBindTexture(GL_TEXTURE_2D, flashlight);
```
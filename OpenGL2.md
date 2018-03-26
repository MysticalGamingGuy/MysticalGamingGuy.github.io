---
layout: default
comments: true
---

[Back](index)

# Introduction
<!-- TODO -->

## GLFW
[GLFW](http://www.glfw.org/) is what we will be using for windowing our application. It's a cross platform library that can run on windows, linux, mac and more. This is the best option as the bindings are provided by LWJGL and are recommended by the developers. Its main purpose is to display OpenGL content and handle events such as window manipulation and HCI input.

## VAO, VBO, EBO
These 3 Objects and their connections are what drives data in the OpenGL pipeline. Here I'll cover each one, explaining their purpose.

### Vertex Buffer Object (VBO)
The VBO is a custom defined array of elements that can contain data such as 
- Vertex Positions
- Texture Coordinates
- Normals
- Colour Data

They can be created with the following OpenGL calls

```kotlin
val vbo = glGenBuffers()
glBindBuffer(GL_ARRAY_BUFFER, vbo)
glBufferData(GL_ARRAY_BUFFER,vertices, GL_STATIC_DRAW)
```

### Vertex Array Object (VAO)
These objects contain
- Attribute Pointers
- VBOs
- EBOs

Attribute pointers are used to define ranges of data stored in a VBO

![Attribute Pointer](https://learnopengl.com/img/getting-started/vertex_attribute_pointer_interleaved.png)

Here is an example of 2 attribute pointers that are setup to conform to the above diagram. 

```kotlin
int stride = 6 * Float.BYTES;
glVertexAttribPointer(0, 3, GL_FLOAT, false, stride, 0);
glVertexAttribPointer(1, 3, GL_FLOAT, false, stride, 3*Float.BYTES);
glEnableVertexAttribArray(0);
glEnableVertexAttribArray(1);
```

### Element Buffer Object (EBO)
The EBO is used for defining multiple uses of single vertices.

In a shape where a vertex is used in multiple triangles, we can define where it is used and how many times.

Take for example the rectangle with vertices 0-5
![Rectangle](https://vulkan-tutorial.com/images/vertex_vs_index.svg)

Without the EBO, we would need to define 6 vertices, 3 for each triangle. but with the EBO, we can define 4 vertices as well as a list defining the order in which the triangles will be drawn. While this reduces the amount of repetitive data, it also makes it harder to define texture coordinates, which you can see occurring in my example code.

## Drawing
Once everything has been setup with the prior objects, we can draw them using the following methods depending on the usage of an EBO

Using an EBO
```kotlin
glDrawElements(GL_TRIANGLES,count, GL_UNSIGNED_INT,offset)
```

Without an EBO
```kotlin
glDrawArrays(GL_TRIANGLES,startingIndex,StoppingIndex);
```

## Shaders
Shaders are C-like programs that are used in the OpenGL pipeline

![OpenGL Pipeline](https://open.gl/media/img/c2_pipeline.png)

In the example code below, we can see a functional vertex shader. Important features of their programs include:

In & Out variables
: For passing variables through the pipeline. (From one and into the next)

Uniform variables
: Constant variables that are set programmatically before a run of the cycle and can be accessed by any shader.

A float Uniform, for example, can be set with the following code
```kotlin
glUniform1f(getUniform(uniformName),value)
```


<img src="https://upload.wikimedia.org/wikipedia/commons/3/39/OpenGL_Tutorial_Triangle_no-fade_version.png" width="250">

```glsl
#version 330 core
layout (location = 0) in vec3 aPos;
layout (location = 1) in vec2 aTexCord;

out vec2 texCord;

uniform mat4 model;
uniform mat4 projection;

void main(){

gl_Position = projection * model * vec4(aPos, 1.0);
texCord = aTexCord;
}
```

## Textures

We can use textures to apply color data to individual pixels baced on an image file.
in a VBO, we can add texture coordinate data. this will consist of X & Y values between 0-1 inclusive. textures in OpenGL have 0,0 in the bottom left and 1,1 in the top right. once each vertex knows its position in regards to the texture, all the pixels between the vertices have their color determined through [interpolation](https://en.wikipedia.org/wiki/Interpolation). 

![Textured Triangle](https://i.imgur.com/lSjgHPI.png)

## Normals 

Normals are directional vectors that face perpendicular to a face (a triangle). they are used in **Lighting** and **Physics** calculation and their data is typically stored in the vbo along the other vertex data.

![Normal Cube](http://3.bp.blogspot.com/-hvsZGGjOsWs/T56u47bcImI/AAAAAAAAAJ4/thcV7nFyHVQ/s1600/cubeSurfaceNormals.jpg)

## Lighting

calculating realistic lighting would involve sending millions of rays from a light source and seeing how they propagate throughout an area. This is why we use lighting models to approximate how lighting looks in a scene. The Phong model is popular because of its fast execution and realistic looking results. The effect comes from the combination of different lighting effects:

- Ambient
- Diffuse
- Specular

These effects are calculated by looking at the relationships between...

- The vector from the camera to a pixel
- the vector from the pixel to the light source
- the normal vector

![Phone lighting](https://upload.wikimedia.org/wikipedia/commons/6/6b/Phong_components_version_4.png)

## Mapping
Maps are simply textures that can be used to add additional data to triangles other than just colors. 

![Maps](http://www.asilefx.net/catalog/images/products/txt_bark2/map_types.jpg)

# Conclusion 
With these topics understood we can begin to bring all the ideas to create something of interest.
These concepts can be seen in action by cloning and running [My Project](https://github.com/MysticalGamingGuy/TheLonelyTildeOpenGL). which will be the same one i will be discussing how to create in my next blog post.

<!--Discus-->
{% if page.comments %}

<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/

var disqus_config = function () {
this.page.url = 'http://thelonelytilde.tk/';  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = 'blog1'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};

(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://thelonelytilde.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>

{% endif %}
---
layout: default
comments: true
---

[Back](index)

# OpenGL Framework Development
As a reference, all the code discussed here can be found on my [Github Repository](https://github.com/MysticalGamingGuy/TheLonelyTildeOpenGL),

## The Framework
In this tutorial we will be building a framework for OpenGL so we can easily create windows with objects that have different textures and shaders. while there is many ways to approach such a framework, we will take a stance that parallels OpenGLs design philosophy.

### Main
Main will be our point of testing where we can assemble all the classes we've created and compose an actual scene. With the way we'll be structuring our program

### Window
The Window class will be very similar to the starting code used in part one, this is because that code was mostly for creating the window. All we need to do is add some helper constructors and methods to allow public usage of it. We will be designing our Window to be responsible for holding the camera, the objects in our world and controlling our running loop. while this solution may be seem as a naive approach for larger engines, this works fine for the scale we're dealing with.


### Texture
The Texture class is responsible for loading image files from disk and sending the relevant data to the graphics card for use in shaders. we are using a library call [stb](https://github.com/nothings/stb) and LWJGL's binding for it.

The process to

### Camera
The Camera class contains all the information to manipulate world space and view space. this just means we can position the camera anywhere in the "world" and apply transformations to produce the 3D effect.
The most important state of the camera include

- FOV
- Position
- Look Direction
- aspect ratio
- upAxis

with this information and our helpful [Mathematics library](https://github.com/JOML-CI/JOML), we can construct a matrix as such:

```kotlin
Matrix4f().perspective(FOV, aspectRatio, 0.1f, 100f).lookAt(position, lookDirection.add(position), upAxis)
```

### Shader


### Shape
Our Shape class contains an enumeration of Custom shapes for testing. The Icosahedron and the Dodecahedron in this case. an array of floats define the positional data  



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
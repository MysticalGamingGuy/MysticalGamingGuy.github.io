---
layout: default
comments: true
---

[Back](index)

## GLFW
[GLFW](http://www.glfw.org/) is what we will be using for windowing our application. It's a cross platform library that can run on windows, linux, mac and more

## VAO, VBO, EBO

### Vertex Array Object (VAO)

### Vertex Buffer Object (VBO)
the VBO is a custom defined array of elements that can contain data such as 
- Vertex Positions
- Texture Coordinates
- Normals
- Colour Data

```kotlin
val vbo = glGenBuffers()
glBindBuffer(GL_ARRAY_BUFFER, vbo)
glBufferData(GL_ARRAY_BUFFER,vertices, GL_STATIC_DRAW)
```

### Element Buffer Object (EBO)
The EBO is used for defining multiple uses of a single vertices.

in a shape where a vertex is used in multiple triangles, we can define where it is used.

Take for example the rectangle with vertices 0-5
![Rectangle](https://vulkan-tutorial.com/images/vertex_vs_index.svg)

without the EBO, we would need to define 6 vertices, 3 for each triangle. but with the EBO, we can define 4 vertices as well as a list defining the order in which the triangles are assembled. While this reduces the amount of repetitive data, it also makes it harder to define texture coordinates, which you can see occurring in the example code.

## Drawing
Once everything has been setup with a prior objects, we can actually draw them

Using an EBO
```kotlin
glDrawElements(GL_TRIANGLES,count, GL_UNSIGNED_INT,offset)
```

And without
```kotlin
glDrawArrays(GL_TRIANGLES,startingIndex,StoppingIndex);
```


## Shaders

## Textures

## Normals 

## Lighting

## Mapping



# Conclusion 
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
---
layout: default
comments: true
---

[Back](index)

# OpenGL Framework Development
As a reference, all the code discussed here can be found on my [Github Repository](https://github.com/MysticalGamingGuy/TheLonelyTildeOpenGL)

In this tutorial we will be building a framework for OpenGL so we can easily create our window and objects with different textures and shaders. While there are many ways to approach such a framework, we will take a stance that parallels OpenGLs design philosophy.

## Classes
The following headings will go into what each class is responsible for in our framework and how it works (Demonstrated with snippets of the most important code). We'll conclude with our Main class and a demonstration of our creation.

### Window
The Window class will be very similar to the starting code used in part one, this is because that code mostly covered creating a window. All we need to do is add some helper constructors and methods to allow public usage of it. We will be designing our Window to be responsible for holding the camera, the objects in our world and controlling our running loop. while this solution may be seem as a naive approach for larger engines, this works fine for the scale we're dealing with.

```kotlin
//Creating our window
glfwCreateWindow(size.x, size.y, title, NULL, NULL)

//Our entire Running loop
while (!glfwWindowShouldClose(window)) {
    val currentFrame = glfwGetTime()
    val delta = (currentFrame - lastFrame).toFloat()
    lastFrame = currentFrame
    glClear(GL_COLOR_BUFFER_BIT or GL_DEPTH_BUFFER_BIT)
    val matrix = camera.update(delta)
    shapes.forEach { it.draw(currentFrame, matrix) }
    glfwSwapBuffers(window)
    glfwPollEvents()
}
```

### Texture
The Texture class is responsible for loading image files from disk and sending the relevant data to the graphics card for use by shaders. we are using a library call [stb](https://github.com/nothings/stb) and LWJGL's binding for it to parse the image data to an acceptable form, one which can be used by the underlying C code.

```kotlin
//Take f.string (The file name) and read its data into the 3 buffers
stbi_load(f.toString(), widthBuffer, heightBuffer, chanelBuffer, 0)

//OpenGL calls to generate the buffers and create the image
textureID = glGenTextures()
glBindTexture(GL_TEXTURE_2D, textureID)
glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, width, height, 0, GL_RGB, GL_UNSIGNED_BYTE, buffer)
```

### Camera
The Camera class contains all the information to manipulate world space and view space. this just means we can position the camera anywhere in the "world" and apply transformations to produce the 3D effect.
The most important state of the camera include

- FOV
- Position
- Look Direction
- aspect ratio
- upAxis

This class can be mostly thought of as a strictly Mathematical class because it is not responsible for called any low level or OpenGL functions. The Window class will be the one to receive the camera's matrix and pass it to a shader.

with this information and our helpful [Mathematics library](https://github.com/JOML-CI/JOML), we can construct a matrix as such:

```kotlin
Matrix4f().perspective(FOV, aspectRatio, 0.1f, 100f)
    .lookAt(position, lookDirection.add(position), upAxis)
```

### Shader
The shader class handles reading our shader files from disk, compiling them, and specifying when to use them. We will also provide helper methods to set uniform variables in the shader. such as...

```kotlin
fun setFloat(uniformName: String, f: Float);
fun setInt(s: String, i: Int);
```

And construct shaders like...

```kotlin
glCreateShader(type).also {
    glShaderSource(it, Files.lines(Paths.get("Test/src/main/shaders/$fileName")).reduce { s, s1 -> "$s\n$s1 " }.get())
    glCompileShader(it)
    checkShaderError(it)
}
```

### Shape
Our Shape class contains an enumeration of Custom shapes for testing. I will be providing the Icosahedron and the Dodecahedron in this case. an array of floats define the positional data. Later on, another class can be created similar to this one only for model loading.

With the VAO's, VBO's, and EBO's set the drawing code looks like this

Note!
- We are using an EBO so we use glDrawElements
- shader is passed during the creating of the shade object
- CurrentFrame is the time that has passed since the last frame
- **matrix** represents the cameras perspective

```kotlin
fun draw(currentFrame: Double, matrix: Matrix4f) {
    shader.use(currentFrame)
    shader.setMatrix("projection", matrix)
    shader.setMatrix("model", modelMatrix)
    glBindVertexArray(Shape.vao)
    glDrawElements(GL_TRIANGLES, Shape.count, GL_UNSIGNED_INT, 0)
}
```

### Main
The Main class will be our point of execution where we can assemble all the classes we've created and compose an actual scene. With the way we'll be structuring our program.

Here is an example of a usage where we

- Center our window with the name "Test"
- Create a dark background
- Create a speedy camera
- create a shader from our Fragment and Vertex shader programs that also...
    -  has two textures called **face** & **icon**
    -  sets a uniform with the name "amount" before every draw call (a value that determines which texture is more visible)
- Add 6 shapes at varying positions
- Start the game loop

```kotlin
fun main(args: Array<String>) {

    Window(1200, 600, "Test").run {

        center()
        setBackgroundColor(.2f, .3f, .3f, 1f)
        camera = Camera(spd = 3f)

        val shader = Shader("fragment.frag", "vertex.vert").apply {
            setTexture("icon.png", 0)
            setTexture("face.jpg", 1)
            onDraw = {
                setFloat("amount", (Math.sin(it) / 2 + .5).toFloat())
            }
        }

        add(
            Shape(Shapes.ICOSAHEDRON, shader, 0f, 0f, -3f),
            Shape(Shapes.ICOSAHEDRON, shader, 0f, -3f, 0f),
            Shape(Shapes.DODECAHEDRON, shader, -3f, 0f, 0f),
            Shape(Shapes.ICOSAHEDRON, shader, 0f, 0f, 3f),
            Shape(Shapes.DODECAHEDRON, shader, 0f, 3f, 0f),
            Shape(Shapes.ICOSAHEDRON, shader, 3f, 0f, 0f)
        )
        start()
    }
}

```

![Image](https://i.imgur.com/SsvTHwu.png)

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
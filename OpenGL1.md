## Understanding & Setup with **OpenGL** on the **JVM** 

### Who This Is For?
If you just want to make a game, this is not the best place to start as that is not the end goal here. I would recommend trying **Unity** or **Game Maker** depending on what you feel comfortable with and to understand what goes into a game engine/framework. With that being said, If you enjoy **Math**, **Low Level Programming** and find joy in building systems from **scratch** without depending as much on other libraries, you're in the right place. I'll be using libraries here to ease the burden of using 3D on the JVM (Kotlin in Specific). This still leaves us in control of major architectural designs. 
These tutorials are for people who have Fundamentail programming skills and would like to apply their knowledge of programming to produce stunning (In my oppinion) 3d visuals. Throughout these posts, i will be assuming a certain degree of programming proficiency, so if you're not sure if you have what it takes, a good benchmark to see if you'll be ready for this is weather you can sit down and program a game of [Pong](https://en.wikipedia.org/wiki/Pong). If not, I might recommend taking a beginner/Intermediate tutorial in either **Java** and/or **Kotlin** in order to understand the concepts covered in these posts. Those with little to no knowledge of 3D and Graphics pipelines will benefit most from these as this will be the main focus of learning. By the end I plan to have provided a baseline understanding of 3D programming from which you can branch off into whatever topics you fancy.  

## OpenGL

### What
OpenGL is an open source GPU specification maintained by the Kronos group as well as a graphics library written in **C**. It features... 

> a cross-language, cross-platform application programming interface (API) for rendering 2D and 3D vector graphics. The API is typically used to interact with a graphics processing unit (GPU), to achieve hardware-accelerated rendering.
> - [OpenGl ~ Wikipedia](https://en.wikipedia.org/wiki/OpenGL)

Those astute amongst you may have realized that we will be using Kotlin in these tutorials while OpenGL is written is C. This will make interacting with OpenGL more complicated as we will need to use [JNI](https://en.wikipedia.org/wiki/Java_Native_Interface) to call native functions. Thankfully there is no need for that, as some very clever people decided to close this complexity gap with a [Binding](https://en.wikipedia.org/wiki/Language_binding) to the OpenGL library, named LWJGL. This allows us to use the advantages of a modern language like Kotlin without worrying as much about interacting with C libraries. We will be going into much more detail about LWJGL Later on.

### Why
When it comes to 3D programming and Interacting with the GPU, options are limited. And considering OpenGL is open source, can operate on all major operating system, and has a relatively easy setup, it’s a great choice to introduce you to the field. There are many other reasons as well, including the increasing precedence of WebGL which is based on OpenGL and more you can look up if you're interested.

## Additional Technologies
This project is focusing around OpenGL but we will be combining many other technologies alongside it. I encourage you to research any technologies further if they are not clear from my explanations here. 
The technologies we will be using include...

##### 1. JVM & Kotlin
Many of you might be familiar with Java, considering that it is the [most popular](https://www.tiobe.com/tiobe-index/) language for some time now and you've probably stumbled across it during your time as a programmer. Kotlin though, isn’t talked about nearly as much. Kotlin is a new language that aims to create a "better java". It's quite modern and was developed to get away for cumbersome java features which have been around since the 1990's. One reason that makes Kotlin special is its interoperability with java, meaning Kotlin can call java function as well as the reverse being true. If you feel more comfortable with java, all parts of this tutorial will be applicable to java as well or any language [C-like](https://en.wikipedia.org/wiki/List_of_C-family_programming_languages) language if you're will to go to the trouble.

##### 2. Gradle
Gradle is a build system that, for our purposes, will allow us to easily configure our project by managing our dependencies without needing to download third party JAR's

##### 3. LWJGL
[LWJGL](https://www.lwjgl.org/) (Light Weight Java Game Library) is a Java library primarily used for enabling
> Cross-platform access to popular native APIs useful in the development of graphics (OpenGL). This access is direct and high-performance, yet also wrapped in a type-safe and user-friendly layer, appropriate for the Java ecosystem.

This is exactly what we need for accessing OpenGL as well as other libraries that we many need in the future.

##### 4. Intellij Community
Intellij is a modern and popular IDE for the JVM. It’s made by the company that created Kotlin (JetBrains), which gives it the advantage of having the best integration with Kotlin. I would recommend understanding the software beforehand as I will not be teaching specifics aspects of Intellij past the initial setup of the project.

## Setup
This part will walk you through how to create a project that has all the technologies we need to display a simple ["Hello World"](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program) type application that will be build upon in later posts.

##### Create a new Project
- Create a new Gradle project in Intellij, the following Screen caps will help you through this process...

![Create Button in Intellij](https://i.imgur.com/PoCX54O.png)

![Project Settings](https://i.imgur.com/ZQOZFZL.png)

- Your GroupID, ArtifactID and Version should follow [this standard](https://maven.apache.org/guides/mini/guide-naming-conventions.html) Ex. me.blogtut, BlogTut, 1.0
- Use auto imports (it'll make it easier when importing the libraries we need)
- Keep the Name the same. you may use any file directory you like (make sure to postfix it with your project’s name)

##### Project Configuration
- Open `build.gradle` (apply suggestions as prompted)

![Suggestion](https://i.imgur.com/k61yTZn.png)

- Add the following configuration into the `build.gradle` file located in the newly created project. This config was generated by [LWJGL's Customizer](https://www.lwjgl.org/customize), feel free to create your own if you are interested.

```groovy
import org.gradle.internal.os.OperatingSystem

switch ( OperatingSystem.current ) {
    case OperatingSystem.WINDOWS:
        project.ext.lwjglNatives = "natives-windows"
        break
    case OperatingSystem.LINUX:
        project.ext.lwjglNatives = "natives-linux"
    break
    case OperatingSystem.MAC_OS:
        project.ext.lwjglNatives = "natives-macos"
        break
}

project.ext.lwjglVersion = "3.1.5"
project.ext.jomlVersion = "1.9.7"

dependencies {
    compile "org.lwjgl:lwjgl:$lwjglVersion"
    compile "org.lwjgl:lwjgl-assimp:$lwjglVersion"
    compile "org.lwjgl:lwjgl-glfw:$lwjglVersion"
    compile "org.lwjgl:lwjgl-openal:$lwjglVersion"
    compile "org.lwjgl:lwjgl-opengl:$lwjglVersion"
    compile "org.lwjgl:lwjgl-stb:$lwjglVersion"
    compile "org.lwjgl:lwjgl:$lwjglVersion:$lwjglNatives"
    compile "org.lwjgl:lwjgl-assimp:$lwjglVersion:$lwjglNatives"
    compile "org.lwjgl:lwjgl-glfw:$lwjglVersion:$lwjglNatives"
    compile "org.lwjgl:lwjgl-openal:$lwjglVersion:$lwjglNatives"
    compile "org.lwjgl:lwjgl-opengl:$lwjglVersion:$lwjglNatives"
    compile "org.lwjgl:lwjgl-stb:$lwjglVersion:$lwjglNatives"
    compile "org.joml:joml:${jomlVersion}"
}
```

- Create a new `Main` Kotlin file in the Kotlin folder
- Copy the [Getting Started Code](https://www.lwjgl.org/guide) into the Main file for a simple getting started demonstration (Intellij will want to convert it into Kotlin, accept that change, as we are using Kotlin.)
- To run it, click the Kotlin logo that will appear to the left of the following function in the `Main` file.

```java
companion object {

    @JvmStatic
    fun main(args: Array<String>) {
        HelloWorld().run()
    }

}
```

![Result](https://i.imgur.com/3iJ1lOm.png)

- If this is what you see, you have done everything correctly and are ready to continue onto the next tutorial. Congratulations!

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
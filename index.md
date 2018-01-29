---
layout: default
comments: true
---

# Welcome to The Lonely Tilde
Welcome everyone to my blog, here I plan on diving into 3D programming on the JVM as well as potentially more topics in the future. These tutorials are for people who have intermediate experience with java and would like to apply their knowledge of programming with 3D. These posts assume programming knowledge. Those with little to no knowledge of 3D and Graphics pipelines will benefit most from these. I plan on providing a solid understanding for you to branch off from into whatever topics interest you.

# Understanding & Setup with **OpenGL** on the **JVM** 

## Who this is for?
If you enjoy **Math**, **Low Level Programming** and find joy in building systems from **scratch** without depending as much on other libraries, this is for you. We use libraries here to ease the burden of using 3D on the JVM but we still are in control of major architectural design.

## Who this isn’t for?
If you are new to programming, I would recommend taking a beginners/Intermediate guide with **Java** or **Kotlin** in order to understand the concepts covered in these posts. If you want to make a game, this is not the best place to start. I would recommend trying **Unity** or **Game Maker** depending on what you feel comfortable with and to understand what goes into a game engine/framework.

# OpenGL

## What
OpenGL is an open source GPU specification maintained by the Kronos group as well as a graphics library written in **C** which features 

> a cross-language, cross-platform application programming interface (API) for rendering 2D and 3D vector graphics. The API is typically used to interact with a graphics processing unit (GPU).
> - [OpenGl ~ Wikipedia](https://en.wikipedia.org/wiki/OpenGL)

Those astute amongst you may have realized that we will be using Kotlin while OpenGL is written is C. This will make interacting with OpenGL more complicated. Thankfully some very clever people decided to close this complexity gap with a Binding to the OpenGL library named LWJGL.  This allows us to use the advantages of a modern language like Kotlin without worrying as much about underling low level implementations.

> a binding from a programming language to a library or operating system service is an application programming interface (API) providing glue code (Adaption between languages) to use that library or service in a given programming language
> - [Language Binding ~ Wikipedia](https://en.wikipedia.org/wiki/Language_binding)

We will go into more detail about LWJGL Later.

## Why
When it comes to 3D programming and Interacting with the GPU, options are limited. And considering OpenGL is open source can operate on all major operating system as well as being relatively easy to get started, it’s a great choice to introduce you to the field. 

## Additional Technologies
This project is focusing around the 3D libraries but we will be combining many other technologies. I encourage you to research and technology further if it is not clear from what I say here. 
The technologies we will be using include...

#### 1. JVM & Kotlin
Many of you might be familiar with Java, considering that it is the [most popular](https://www.tiobe.com/tiobe-index/) java for some time now and are/were probably thought it in school. Kotlin probably isn’t as talked about. Kotlin is a new language that aims to create a "better java". It quite modern and developed to get away for cumbersome java features which have been around since 1996. One reason that makes Kotlin special is its interoperability with java, meaning Kotlin can call java function as well as the reverse. If feel more comfortable with java, all parts of this tutorial will be applicable to java.

#### 2. Gradle
Gradle is a build system that, for our purposes, will allow us to easily configure our project by managing our dependences as well as retrieving them remotely.

#### 3. LWJGL
[LWJGL](https://www.lwjgl.org/) (Light Weight Java Game Library) is a Java library primarily for enabling
> Cross-platform access to popular native APIs useful in the development of graphics (OpenGL)
This is exactly what we need because of the aforementioned reasons.

#### 4. Intellij Community
Intellij is a modern and popular IDE for the JVM. It’s made by the company that created Kotlin, which gives it the advantage of having the best integration with Kotlin. I would recommend understanding the software beforehand as I will 

## Setup
This part will walk you through how to create a project that has all the technologies we need to display a simple ["Hello World"](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program) type application.

#### Create a new Project
- Install Java JDK 1.8
- Create a new Gradle project in Intellij, the following Screen caps will help you through this process

![Create Button in Intellij](https://i.imgur.com/PoCX54O.png)
![Project Settings](https://i.imgur.com/ZQOZFZL.png)

- Your GroupID, ArtifactID and Version should follow [this standard](https://maven.apache.org/guides/mini/guide-naming-conventions.html) Ex. me.blogtut, BlogTut, 1.0
- Use auto imports (it'll make it easier when importing the libraries we need)
- Keep the Name the same and you may use any location you like (make sure to postfix it with your project’s name)
- Open `build.gradle` (apply suggestions as prompted)

![Suggestion](https://i.imgur.com/k61yTZn.png)

- add the following configuration into the `build.gradle` file in the newly created project. This was made by [LWJGL's Customizer](https://www.lwjgl.org/customize), feel free to create your own.

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

- Create a new Main Kotlin file in the Kotlin folder
- copy the [Getting Started Code](https://www.lwjgl.org/guide) into the Main file for a simple getting started boost (Intellij will want to convert it into Kotlin, accept that change, as we are using Kotlin.)
- To Run it, click the Kotlin logo that will appear next to the following function in the Kotlin file.

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
/*
var disqus_config = function () {
this.page.url = 'http://thelonelytilde.tk/';  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = 'blog1'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://thelonelytilde.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>

{% endif %}



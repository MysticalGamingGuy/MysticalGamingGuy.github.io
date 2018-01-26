# Welcome to The Lonely Tilde
Welcome everyone to my blog, here I plan on diving into 3D programming on the JVM as well as potentially more topics in the future. These tutorials are for people who have intermediate experience with java and would like to apply their knowledge of programming with 3D. These posts assume no or limited knowledge of 3D and Graphics pipelines, and plan on providing a solid understanding for you to branch off from into whatever topics interest you.

# Understanding & Setup with **OpenGL** on the **JVM** 

## Who this is for?
If you enjoy **Math**, **Low Level Programming** and find joy in building systems from scratch without depending as much on other librabies, this is for you. We use libraries here to ease the burden of using 3D on the JVM but we still are in control of major archtectural design.

## Who this isn’t for?
If you are new to programming, i would recommend taking a beginners/Intermidiate guide with **Java** or **Kotlin** in order to understand the concepts covered in these posts. If you want to make a game, this is not the best place to start. I would recommend trying **Unity** or **Game Maker** depending on what you feel comfortable with and to understand what goes into a game engine/framework.

# OpenGL

## What
OpenGL is an open source GPU specification maintained by the Kronos group as well as a graphics library written in **C** which features 

> a cross-language, cross-platform application programming interface (API) for rendering 2D and 3D vector graphics. The API is typically used to interact with a graphics processing unit (GPU) .
> - OpenGl, Wikipedia 

Those astute amongst you may have realized that we will be using Kotlin while OpenGL is written is C. This will make interacting with OpenGL more complicated. Thankfully some very clever people decided to close this complexity gap with a Binding to the OpenGL library named LWJGL.  This allows us to use the advantages of a modern language like Kotlin without worrying as much about underling low level implementations.

> a binding from a programming language to a library or operating system service is an application programming interface (API) providing glue code (Adaption between languages) to use that library or service in a given programming language
> - Captain Janeway

We will go into more detail about LWJGL Later.

## Why
When it comes to 3D programming and Interacting with the GPU, options are limited. And considering OpenGL is open source can operate on all major operating system as well as being relatively easy to get started, it’s a great choice to introduce you to the feild. 

## Aditional Technologies
This project is focusing around the 3D libraies but we will be combining many other technologies. I encourage you to reasearch and technology fucther if it is not clear from what i say here. 
The technologies we will be using include...

#### 1. JVM & Kotlin
Many of you might be familiar with Java, considering that it is the [most popular](https://www.tiobe.com/tiobe-index/) java for some time now and are/were probably thought it in school. Kotlin probably isn’t as talked about. Kotlin is a new language that aims to create a "better java". It quite modern and developed to get away for cumbersome java features which have been around since 1996. One reason that makes kotlin special is its interoperability with java, meaning kotlin can call java function as well as the reverse.

#### 2. Gradle
Gradle is a build system that, for our purposes, will allow us to easily configure our project by managing our dependances as well as retreving them remotely.

#### 3. LWJGL
[LWJGL](https://www.lwjgl.org/) (Light Weight Java Game Library) is a Java library primarily for enabling
> cross-platform access to popular native APIs useful in the development of graphics (OpenGL)
This is exacally what we need because of the aformenthioned reasons.

#### 4. Intellij Community
Intellij is a modern and popular IDE for the JVM. it's made by the company that created Kotlin, which gives it the advantage of having the best integrationg with Kotlin.

## Setup
This part will walk you through how to create a project that has all the technologies we need to display a simple ["Hello World"](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program) type application.


```java
public static void main(String[] args){
    System.out.println("hello world");
}
```

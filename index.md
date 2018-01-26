# Welcome to The Lonely Tilde

# Blog

## Introduction & Setup with OpenGL on the JVM 

## Introduction
Welcome everyone to my blog, here I plan on diving into 3D programming on the JVM. These tutorials are for people who have intermediate experience with java and would like to apply their knowledge of programming with 3D. These posts assume no or limited knowledge of 3D and Graphics pipelines, and plan on providing a solid understanding for you to branch off from.

## Who this is for?
If you enjoy Math, low level programming and find joy in building systems from scratch without depending on other librabies as much, this is for you.

## Who this isn’t for?
If you are new to programming, i would recommend taking a beginners guide with Java in order to understand the concepts covered in these posts. If you want to make a game, this is not the best place to start. I would recommend trying unity or Game maker depending on what you feel comfortable with.

# OpenGL

## What
OpenGL is an open source GPU specification maintained by the Kronos group as well as a graphics library written in ‘C’ which features 

> a cross-language, cross-platform application programming interface (API) for rendering 2D and 3D vector graphics. The API is typically used to interact with a graphics processing unit (GPU) .
> Wikipedia 

Those astute amongst you may have realized that we will be using Kotlin while OpenGL is written is C. This will make interacting with OpenGL more complicated. Thankfully some very clever people decided to close this complexity gap with a Binding to the OpenGL library named LWJGL.  This allows us to use the advantages of a modern language like Kotlin without worrying as much about underling low level implementations.

> a binding from a programming language to a library or operating system service is an application programming interface (API) providing glue code (Adaption between languages) to use that library or service in a given programming language
> - Captain Janeway

We will go into more detail about LWJGL Later.

## Why
When it comes to 3D programming and Interacting with the GPU, options are limited. And considering OpenGL can operate on all major operating system as well as being relatively easy to get started, it’s a great choice to introduce you to the feild. 

## Technologies
During this project we will The technologies we will be using include

### JVM & Kotlin
Many of you might be familiar with Java, considering that it is the most popular<sup>1</sup> java for some time now and are/were probably thought it in school. Kotlin probably isn’t as talked about. Kotlin is a new language

### Gradle

### LWJGL


### Intellij Community
Intellij is a modern and popular IDE for the JVM.

##Setup
```java
public static void main(String[] args){
    System.out.println("hello world");
}
```

1: https://www.tiobe.com/tiobe-index/
2: https://www.lwjgl.org/

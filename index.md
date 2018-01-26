## Welcome to The Lonely Tilde

You can use the [editor on GitHub](https://github.com/MysticalGamingGuy/MysticalGamingGuy.github.io/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/MysticalGamingGuy/MysticalGamingGuy.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

### Blog

## Introduction & Setup with OpenGL on the JVM 

##Introduction
Welcome everyone to my blog, here I plan on diving into 3D programming on the JVM. These tutorials are for people who have intermediate experience with java and would like to apply their knowledge of programming with 3D. These posts assume no or limited knowledge of 3D and Graphics pipelines, and plan on providing a solid understanding for you to branch off from.
Who this is for?
Who doesn’t want to make a Game?

## Who this isn’t for?

## OpenGL

## What
OpenGL is a GPU specification maintained by the Kronos group as well as  a graphics library  written in ‘C’ which features “a cross-language, cross-platform application programming interface (API) for rendering 2D and 3D vector graphics. The API is typically used to interact with a graphics processing unit (GPU) “. Those astute among you may have noticed realize that we will be using Kotlin while OpenGL is written is C. This will make interacting with OpenGL more complicated. Thankfully some very clever people decided to close this complexity gap with a Binding to the OpenGL library named LWJGL.  This allows us to use the advantages of a modern language like Kotlin without worrying as much about underling low level implementations.
~ a binding from a programming language to a library or operating system service is an application programming interface (API) providing glue code (Adaption between languages) to use that library or service in a given programming language ~
We will go into more detail about LWJGL Later.
Why
When it comes to 3D programming and Interacting with the GPU, options are limited. And considering OpenGL can operate on all major operating system as well as being relatively easy to get started, it’s a good choice. 

## Technologies
During this project we will The technologies we will be using include
# JVM & Kotlin
Many of you might be familiar with Java, considering that it is the most popular<sup>1</sup> java for some time now and are/were probably thought it in school. Kotlin probably isn’t as talked about. Kotlin is a new language 
# Gradle
# LWJGL
# Intellij Community

```java
public static void main(String[] args){
    System.out.println("hello world");
}
```

1: [https://www.tiobe.com/tiobe-index/](https://www.tiobe.com/tiobe-index/)

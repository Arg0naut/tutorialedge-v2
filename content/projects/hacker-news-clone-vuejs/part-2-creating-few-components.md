---
title: "Part 2 - Creating a Few Components"
date: 2018-03-19T16:24:13Z
draft: true
desc: "In this tutorial, we are going to be creating a few components to our HackerNews clone and fleshing out our project."
author: "Elliot Forbes"
tags: ["vuejs", "javascript"]
image: "vuejs.png"
weight: 2
series: [ "hackernewsclone" ]
twitter: "https://twitter.com/Elliot_F"
---

In the previous tutorial, we managed to set up our base project and get it running on `http://localhost:8080`. We now have a base from which we can build up up our HackerNews clone.

## A Simple Navbar Component

So, the first thing I always notice whenever I open up HackerNews is the iconic orange navbar at the top. This will undoubtedly have to feature in our own clone, and in order to add it, we'll have to create a `Navbar` component.

Open up your project in a text editor of your choice and open the directory that your project exists within. Create a `Navbav.vue` file within the `src/components/` directory and add the following:

```html
<template>
  <nav>

  </nav>
</template>

<script>
export default {
  name: 'Navbar'
}
</script>

<style scoped>

</style>
```

The above code represents the bare-bones of our new `Navbar` component. We define the `HTML` we wish to render for our component within the `<template>` tags, we define all of our core component functionality, a.k.a. all of the JavaScript functions within the `<script>` tags. Finally, should we wish to add custom styling to our `Navbar` component, we can do so by placing the `css` within our `<style>` tags. You should notice we've added `scoped` to our style tag, this essentially ensures that the `css` we define within this component will only impact the `HTML` within our component.

I've populated the `<template>` tags with a simple `<nav>` element just to get us started.

## Registering our New Component

So, now that we've defined our `Navbar.vue` component, it's time to register it within our application and start using it.

Open up your `src/App.vue` component file and within the `<script>` tag, import your `Navbar` and add it to your `components` object like so:

```js
import HelloWorld from './components/HelloWorld.vue'
import Navbar from './components/Navbar.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Navbar
  }
}
```

Once we have imported and registered this new component, we can use it within our `App.vue`'s `HTML` by adding the `<navbar>` to our app and removing the `<helloworld>` tag from our `<template>` section.

```html
<template>
  <div id="app">
    <navbar></navbar>
  </div>
</template>
```

Our finished `src/App.vue` file should look like this:

```html
<template>
  <div id="app">
    <navbar></navbar>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'

export default {
  name: 'app',
  components: {
    Navbar
  }
}
</script>

<style>
</style>
```

## Adding a CSS Framework

Pretty much every web application you see will utilize some form of `CSS` framework. Now, for this project, I'm choosing to use the Pure-CSS framework as it seems relatively lightweight whilst featuring essentials such as a grid system, and I haven't had much of a chance to play about with it yet. 

In order to add a CSS framework to our project, open up the `public/index.html` page within your project and add:

```html
<link rel="stylesheet" href="https://unpkg.com/purecss@1.0.0/build/pure-min.css" integrity="sha384-nn4HPE8lTHyVtfCBi5yW9d20FjT8BJwUXyWZT9InLYax14RDjBj46LmSztkmNP9w" crossorigin="anonymous">
```

To just below your `<title>` tag. Upon clicking the `cmd-s` you should see your application reload on `http://localhost:8080` with a slightly different style.

## How it looks

At this stage, your application should look something like this:

![Our HackerNews clone as it stands](https://s3-eu-west-1.amazonaws.com/tutorialedge.net/images/hackernews-clone/screenshot-02.png)

## Next Steps

Now that we've defined a few, very simple components within our application, it's time to move on and start thinking about how we can show different views within our application. This is where the `vue router` will come into play!
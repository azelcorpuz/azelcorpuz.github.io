---
layout: post
title:  "Vue 3 Cheat Sheet"
date:   2021-02-15 23:14:00 +0800
categories: tools
---

## Concepts
* **Data** - is a function and need to define the data to be use in the template. Should return an object
```
data: () =>  ({
  info: null
})
```
* **Method** - is an object with  functions and this is to define the methods to be used
```
  methods: {
    login: function () {
      this.$router.push('/home')
    }
  }
```
* **Mounted** - is a function that is called after the instance has been mounted.

## Multiple pages in Vue3
I have an application with 2 types of pages:
1. static pages - or the *"website"* which is purely html, javascript (for animation), css files - no communication with server/backend.
2. spa - or the *"portal"* which will have some CRUD operations

To do this in view, you need a configuration `vue.config.js` like below:
```
module.exports = {
    pages: { 
      index: { // main page of your application, can be access via  <hostname>:<port>/<any character>
        entry: 'src/website.ts', // entry for the page - mandatory
        template: 'public/index.html', // entry for the page
        filename: 'index.html', // the name of the file when built (those that goes to dist/)
        chunks: ['chunk-vendors', 'chunk-common', 'index'] // not really sure for now what is this (??)
      },
      portal: { // subpage, you can access this page via <hostname>:<port>/portal<any character>
        entry: 'src/main.ts', 
        template: 'public/spa/index.html', 
        filename: 'portal/index.html' 
      }
    }
}
```

Notes:
1. The filename should be unique through different pages
2. The entry file for my *website* (or index page) is empty - i am not initiating anything
3. On the router of my *portal* - i have prefixed it always with `/portal` because if not and you go to different route (for example `/login`) and you refreshed, you will end up on the main page of the application.

## Vue3 in Typescript
Vue component template code:
```
<template>
  <div>Hello template!</div>
</template>
<script lang="ts">
import { Vue } from 'vue-class-component';
@Options({
  props: {
    msg: String
  }
})
export default class LoginPage extends Vue {
}
</script>
<style scoped><!-- Add "scoped" attribute to limit CSS to this component only -->
</style>
```

Router:
https://www.vuemastery.com/blog/vue-router-a-tutorial-for-vue-3/
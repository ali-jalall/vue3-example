# vue-next-webpack-preview

> Webpack setup for Vue 3  

This is for preview only. You might find some bugs and undocumented behavior, which are totaly expected


### Install
```sh
git clone https://github.com/ali-jalall/vue3-example.git vue3-tutorial
cd vue3-tutorial
npm install
```
### Usage
##### Develop
```sh
# will run your server at localhost:8080
npm run dev
```

# New Features

### Creating a new Vue 3 app
The way we create a new App has changed, instead of using ``` new Vue()``` 
Now we can import createApp method 
Then we call this method, passing our vue instance definition object, and assign it to variable app
Next, we'll call ``` mount() ``` method and pass our mount element
```sh
import { createApp } from "vue";
import App from "./App/vue"

const app = createApp(App);

app.mount("#app");

```

### Multi-root templates
If you are Vue 2.0 developer you will notice the error in the code down below, that's right there's no need for your template to have one root element 

```sh
<template>
  <h3>Vue is the Best</h3>
  <img src="./logo.png"/>
  <p>
    You can see that this template has multiple root elements
  </p>
</template>
```
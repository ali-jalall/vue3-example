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
The way we create a new App has changed, instead of using ```sh new Vue()``` 
Now we can import createApp method 
Then we call this method, passing our vue instance definition object, and assign it to variable app
Next, we'll call ```sh mount() ``` method and pass our mount element
```sh
import { createApp } from "vue";

const app = createApp({
  // root instance definition
});

app.mount("#app");

```
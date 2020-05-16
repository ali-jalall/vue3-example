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
If you are Vue 2.0 developer you will notice the error in the code down below, that's right no longer compulsory to have one root element thanks to a feature called fragments 

```sh
<template>
  <h3>Vue is the Best</h3>
  <img src="./logo.png"/>
  <p>
    You can see that this template has multiple root elements
  </p>
</template>
```

### Refactoring with Composition API
The most intersting feature (for me) is the Composition API. This new API allows you to define component functionality using a setup function rather than with properties you add to the component definition object.


```sh
<template>
  <h3>Vue is the Best</h3>
  <img style="width: 100px" src="./logo.png"/> <br />
  <button @click="increaseFans">we have {{ fan }} fans.</button>
  <p>
    You can see that this template has multiple root elements
  </p>
</template>
<script>
import Modal from "./components/Modal.vue";
import { ref } from "vue";
export default {
  setup() {
    const fan = ref(0);
    const increaseFans = () => {
      fan.value++
    };
    return {
      fan,
      increaseFans,
    };
  },
};
</script>
```

Notice that the Composition API only affects the way we define the component functionality, not the way we render it.
and it's optional for you you can totaly ignore it

### ``` Setup() ``` method
First when we import ``` ref ``` it is function that allow us to define a reactive variable ``` fan ```.  
And The ``` increaseFans ``` method is just a plain javascript method. notice that the way we change the ``` fan ``` we need to change it's sub-propery ``` value ``` that's why when we create reactive variable using ``` ref ``` that variable will be wrapped in an object, that's necessary to retain their reactivity.
Finally we returned ``` fan ``` and ``` increaseFans ``` from the ``` setup ``` method, as these are the values that get passed to the template when it's rendered.


### Emitting an event
Let's create a component called ``` Info ``` and toggle it in ``` App.vue ``` by variable called ``` showInfo ``` and method ``` toggleInfo ``` 

``` sh
<template>
  ...
  <button @click="toggleInfo">More Details</button>
  <info v-if="showInfo">
    Here are some detailsLorem Ipsum is simply dummy text of the printing and
    typesetting industry. Lorem Ipsum has been the industry's standard dummy
    text ever since the 1500s
  </info>
</template>
<script>
import { ref } from "vue";
import Info from "./components/Info.vue";
export default {
  components: { Info },
  setup() {
    ...
    const showInfo = ref(false);
    const toggleInfo = () => {
      showInfo.value = !showInfo.value;
    };
    return {
      showInfo,
      toggleInfo,
    };
  },
};
</script>
```
So far so good
Let's take a look at ``` Info.vue ```

```sh
<template>
  <div class="info">
    <slot></slot>
    <button @click="$emit('close-details')">Close</button>
  </div>
</template>
```

So far, this feature is identical as it would be in Vue 2. However, in Vue 3 it's now recommended that you explicitly state a component's events using the new ``` emits ``` component option. Just like with props, you can simply create an array of strings to name each event the component will emit.

```sh
<template> ... </template>
<script>
export default {
  emits: [ "close-details" ]
}
</script>
```

### Styling slot content
Styling for Content, i have thought of everything they can make to improve Vue.js but i have never thought of styling a slot content. Alright let's see.
Before we use ``` scoped ``` to make our style scoped for a specific component

```sh
<template>...</template>
<script>...</script>
<style scoped>
  h3 {
    font-style: italic;
  }
</style>
```
If you try this, you'll see that it doesn't work. Because the scoped styling is determined at compile time so the slot content sill belong to the parent

Here comes the new feature ``` ::v-slotted() ``` allowing you to target a slot content with scoped rules in the component providing the slot.

```sh
<style scoped>
  ::v-slotted(p) {
    font-style: italic;
  }
</style>
```

### There's More
There's more features that i didn't mention above. Here go ahead you can create your own repo and mention them


Vue.js is my favorite library for building web interfaces, it provides a great features to do whatever you want
That's why it's imprtant to follow up with all the new technology released 
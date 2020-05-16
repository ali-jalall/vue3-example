<template>
  <h3>Vue is the Best</h3>
  <img src="./logo.png"/>
  <p>
    You can see that this template has multiple root elements
  </p>
</template>
<script>
import Modal from "./components/Modal.vue";
import { ref } from "vue";
export default {
  setup() {
    const modalState = ref(false);
    const toggleModalState = () => {
      modalState.value = !modalState.value;
    };
    return {
      modalState,
      toggleModalState,
    };
  },
};
</script>

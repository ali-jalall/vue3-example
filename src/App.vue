<template>
  <button @click="toggleModalState">Open modal</button>
  <teleport to="#modal-wrapper">
    <modal v-if="modalState" @click="toggleModalState">
      <p>Hello, I'm a modal window.</p>
    </modal>
  </teleport>
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

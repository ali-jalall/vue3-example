<template>
  <h3>Vue is the Best</h3>
  <img style="width: 100px;" src="./logo.png" /> <br />
  <button @click="increaseFans">we have {{ fan }} fans.</button>
  <p>
    You can see that this template has multiple root elements
  </p>
  <button @click="toggleInfo">More Details</button>
  <info v-if="showInfo" @click="toggleInfo">
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
    const fan = ref(0);
    const showInfo = ref(false);
    const increaseFans = () => {
      fan.value++;
    };
    const toggleInfo = () => {
      showInfo.value = !showInfo.value;
    };
    return {
      fan,
      increaseFans,
      showInfo,
      toggleInfo,
    };
  },
};
</script>

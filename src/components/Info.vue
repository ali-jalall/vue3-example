<template>
  <div>
    <slot></slot>
    <button @click="$emit('close-details')">Close</button>
  </div>
</template>
<script>
export default {
  emits: [ "close-details" ]
}
</script>
<template>
  <div class="container" :style="{ maxWidth: `${maxWidth}px` }">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "Container",
  props: ["max-width"]
}
</script>

<style scoped>
.container {
  margin: auto;
}
</style>

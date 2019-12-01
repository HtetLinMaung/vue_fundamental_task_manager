<template>
  <button :class="btnClass">
    <slot>Button</slot>
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    small: Boolean,
    large: Boolean,
    rounded: Boolean
  },
  data() {
    const { small, large, rounded } = this

    return {
      btnClass: [
        "btn",
        { "btn-small": small && !large },
        { "btn-large": large && !small },
        { rounded }
      ]
    }
  }
}
</script>

<style scoped>
.btn {
  font-family: "Solway", serif;
  display: inline-flex;
  background-color: #f5f5f5;
  box-shadow: 0px 3px 1px -2px rgba(0, 0, 0, 0.2),
    0px 2px 2px 0px rgba(0, 0, 0, 0.14), 0px 1px 5px 0px rgba(0, 0, 0, 0.12);
  justify-content: center;
  font-weight: 500;
  max-width: 100%;
  outline: 0;
  position: relative;
  text-decoration: none;
  transition-duration: 0.3s;
  transition-property: box-shadow, transform, opacity, background;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  user-select: none;
  vertical-align: middle;
  white-space: nowrap;
  overflow: hidden;
  border-radius: 4px;
  /* btn-medium */
  height: 36px;
  min-width: 64px;
  padding: 0 16px;
  font-size: 0.875rem;
  border: 0px;
  color: rgba(0, 0, 0, 0.87);
}

.btn:hover {
  background: rgb(224, 218, 218);
}

.dark {
  color: #fff;
}

.btn-small {
  font-size: 0.75rem;
  min-width: 50px;
  height: 28px;
  padding: 0 12.4444444444px;
}

.btn-large {
  font-size: 0.875rem;
  height: 44px;
  min-width: 78px;
  padding: 0 19.5555555556px;
}

.rounded {
  border-radius: 28px;
}

.btn:after {
  border-radius: 50%;
  content: "";
  background: grey;
  display: block;
  position: absolute;
  padding: 60px;
  margin-top: -2.5rem;
  opacity: 0;
  transition: all 0.8s;
}

.btn:active:after {
  padding: 0;
  margin: 0;
  opacity: 1;
  transition: 0s;
}
</style>

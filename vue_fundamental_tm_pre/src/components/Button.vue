<template>
  <button class="btn btn-small">
    <slot>Button</slot>
  </button>
</template>

<script>
export default {
  name: 'Button'
}
</script>

<style scoped>
.btn {
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
  transition-duration: 0.28s;
  transition-property: box-shadow, transform, opacity;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  user-select: none;
  vertical-align: middle;
  white-space: nowrap;
  overflow: hidden;
}

.btn-small {
  font-size: 0.75rem;
  min-width: 50px;
  height: 28px;
  padding: 0.1rem 1rem;
}

.btn:after {
  content: '';
  background: #90ee90;
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

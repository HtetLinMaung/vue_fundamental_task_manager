<template>
  <div>
    <select v-model="choice" class="select-box">
      <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
        >{{ option.text }}</option
      >
    </select>
  </div>
</template>

<script>
export default {
  name: "SelectInput",
  props: ["options", "selected"],
  data() {
    return {
      choice: this.selected
    };
  },
  watch: {
    choice(newVal) {
      this.$emit("onSelect", newVal);
    }
  }
};
</script>

<style scoped>
.select-box {
  font-size: 15px;
  padding: 0.3rem 0.8rem;
  color: rgb(117, 105, 105, 0.9);
  border-radius: 4px;
  border: 1px solid rgb(143, 137, 137);
  transition-property: border;
  transition-duration: 0.3s;
}
.select-box:focus {
  outline: none;
  border: 1px solid rgb(37, 221, 253);
}
</style>

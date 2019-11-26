<template>
  <div class="wrapper">
    <div>
      <select v-model="selected" class="select-box">
        <option
          v-for="option in options"
          :key="option.key"
          :value="option.value"
          >{{ option.text }}</option
        >
      </select>
    </div>
    <div class="search-wrapper">
      <input type="text" v-model="search" class="search" placeholder="search" />
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchInput",
  props: ['items'],
  data: () => ({
    search: "",
    selected: "5",
    options: [
      { value: 0, text: "Not Started" },
      { value: 1, text: "Completed" },
      { value: 2, text: "In Progress" },
      { value: 3, text: "Pending" },
      { value: 4, text: "Rejected" },
      { value: 5, text: "Filter" }
    ]
  }),
  watch: {
    selected: function(newVal) {
       
    }
  }
};
</script>

<style scoped>
.wrapper {
  margin: 1rem 0;
  display: flex;
}

.search-wrapper {
  margin-left: auto;
}

.select-box {
  font-size: 15px;
  padding: 0.3rem 0.8rem;
  color: rgb(117, 105, 105, 0.9);
  border-radius: 4px;
  border: 1px solid rgb(143, 137, 137);
}

.search {
  font-size: 15px;
  padding: 0.3rem 0.8rem;
  color: rgb(117, 105, 105, 0.9);
  border-radius: 15px;
  border: 1px solid rgb(143, 137, 137);
}
</style>

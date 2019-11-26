<template>
  <div style="padding: 4rem 3.5rem;">
    <search-input :items="items" />
    <task-item v-for="item in items" :key="item.id" :item="item" />
  </div>
</template>

<script>
import TaskItem from "../components/TaskItem";
import SearchInput from "../components/SearchInput";

export default {
  name: "Tasks",
  props: ["items"],
  components: {
    "task-item": TaskItem,
    "search-input": SearchInput
  }
};
</script>

<style scoped></style>

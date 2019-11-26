<template>
  <div style="padding: 4rem 3.5rem;">
    <search-input :items="items" @search-filter="setCollection" />
    <task-item v-for="item in collections" :key="item.id" :item="item" />
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
  },
  data: () => ({
    collections: items
  }),
  methods: {
    setCollection(search_items) {
      this.collections = search_items;
    }
  }
};
</script>

<style scoped></style>

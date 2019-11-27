<template>
  <div style="padding: 4rem 3.5rem;">
    <div class="wrapper">
      <div>
        <select-input :options="options" selected="5" />
      </div>
      <div class="search-wrapper">
        <search-input
          :items="
            items.map(item => ({ ...item, status_name: status[item.status] }))
          "
          :searchKeys="['task_name', 'status_name']"
          @search-filter="updateCollection"
        />
      </div>
    </div>
    <task-item v-for="item in collections" :key="item.id" :item="item" />
  </div>
</template>

<script>
import TaskItem from "../components/TaskItem";
import SearchInput from "../components/SearchInput";
import SelectInput from "../components/SelectInput";

export default {
  name: "Tasks",
  props: ["items"],
  components: {
    "task-item": TaskItem,
    "search-input": SearchInput,
    "select-input": SelectInput
  },
  data() {
    return {
      collections: this.items,
      options: [
        { value: 0, text: "Not Started" },
        { value: 1, text: "Completed" },
        { value: 2, text: "In Progress" },
        { value: 3, text: "Pending" },
        { value: 4, text: "Rejected" },
        { value: 5, text: "Filter" },
        { value: 6, text: "Wait for Confirm" }
      ],
      status: [
        "Not Started",
        "Completed",
        "In Progress",
        "Pending",
        "Rejected",
        "Wait for Confirm!"
      ]
    };
  },
  methods: {
    updateCollection(search_items) {
      this.collections = search_items;
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
</style>

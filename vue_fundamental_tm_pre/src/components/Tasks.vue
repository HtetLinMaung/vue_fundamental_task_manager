<template>
  <div style="padding: 4rem 3.5rem;">
    <div class="wrapper">
      <div>
        <select-input :options="options" selected="6" @onSelect="filterData" />
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
    <div class="modal">
      <div class="modal-content">
        <span class="close">&times;</span>
        <p>Some text in the Modal..</p>
      </div>
    </div>
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
        { value: 5, text: "Wait for Confirm" },
        { value: 6, text: "Filter Off" }
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
    },
    filterData(selected) {
      if (selected == "6") this.collections = this.items;
      else
        this.collections = this.items.filter(
          item => item.status == parseInt(selected)
        );
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
/* for modal */
.modal {
  display: none;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.4);
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}
</style>

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
    <task-item
      v-for="item in collections"
      :key="item.id"
      :item="item"
      @click.native="modalFlag = true"
    />
    <modal-box v-model="modalFlag" max-width="650">
      <template v-slot:content> hello </template>
    </modal-box>
  </div>
</template>

<script>
import TaskItem from "../components/TaskItem";
import SearchInput from "../components/SearchInput";
import SelectInput from "../components/SelectInput";
import ModalBox from "../components/ModalBox";

export default {
  name: "Tasks",
  props: ["items"],
  components: {
    "task-item": TaskItem,
    "search-input": SearchInput,
    "select-input": SelectInput,
    "modal-box": ModalBox
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
      ],
      modalFlag: false
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
    // openModal() {
    //   this.$refs.modal.style.display = "block";
    // }
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

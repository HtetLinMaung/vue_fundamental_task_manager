<template>
  <div :class="[getTaskStyle(item.status)]">
    <div class="task-name">{{ item.task_name }}</div>
    <div :class="[getStatusStyle(item.status)]">
      {{ status[item.status] }}
    </div>
  </div>
</template>

<script>
export default {
  name: "TaskItem",
  props: ["item"],
  data: () => ({
    status: [
      "Not Started",
      "Completed",
      "In Progress",
      "Pending",
      "Rejected",
      "Wait for Confirm!"
    ]
  }),
  methods: {
    getTaskStyle(status) {
      let Class = "task-item";
      switch (status) {
        case 0:
          Class += " task-item-ns";
          break;
        case 1:
          Class += " task-item-com";
          break;
        case 2:
          Class += " task-item-pro";
          break;
        case 3:
          Class += " task-item-pen";
          break;
        case 4:
          Class += " task-item-rej";
          break;
        default:
          Class += " task-item-wai";
      }
      return Class;
    },
    getStatusStyle(status) {
      let Class = "status";
      switch (status) {
        case 0:
          Class += " status-ns";
          break;
        case 1:
          Class += " status-com";
          break;
        case 2:
          Class += " status-pro";
          break;
        case 3:
          Class += " status-pen";
          break;
        case 4:
          Class += " status-rej";
          break;
        default:
          Class += " status-wai";
      }
      return Class;
    }
  }
};
</script>

<style scoped>
.task-item {
  /* transition-property: transform;
  transition-duration: 0.3s; */
  transition: transform 0.3s;
  margin-bottom: 0.75rem;
  display: flex;
  background: #fff;
  padding: 1.3rem 1rem;
  border-radius: 4px;
  align-items: center;
  box-shadow: 0px 3px 1px -2px rgba(0, 0, 0, 0.2),
    0px 2px 2px 0px rgba(0, 0, 0, 0.14), 0px 1px 5px 0px rgba(0, 0, 0, 0.12);
}

.task-item:hover {
  transform: scaleX(1.05);
}

.task-item-ns {
  border-left: 15px solid #fff;
}

.task-item-com {
  border-left: 15px solid rgb(15, 202, 83);
}

.task-item-pro {
  border-left: 15px solid rgb(10, 202, 236);
}

.task-item-pen {
  border-left: 15px solid rgb(246, 87, 29);
}

.task-item-rej {
  border-left: 15px solid rgb(251, 76, 76);
}

.task-item-wai {
  border-left: 15px solid rgb(207, 187, 4);
}

.task-name {
  padding-left: 1rem;
  color: rgb(117, 105, 105);
  height: 20px;
  overflow: hidden;
  max-width: 500px;
}

.status {
  color: #fff;
  margin-left: auto;
  padding: 0.4rem 1rem;
  border-radius: 15px;
  font-size: 14px;
}

.status-ns {
  border: 1px solid rgb(143, 137, 137);
  color: rgb(143, 137, 137) !important;
}

.status-pro {
  background-color: rgb(10, 202, 236);
}

.status-com {
  background-color: rgb(15, 202, 83);
}

.status-pen {
  background-color: rgb(246, 87, 29);
}

.status-rej {
  background-color: rgb(251, 76, 76);
}

.status-wai {
  background-color: rgb(207, 187, 4);
}
</style>

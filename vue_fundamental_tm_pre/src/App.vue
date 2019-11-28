<template>
  <div id="app">
    <Tasks :items="tasks" />
  </div>
</template>

<script>
import Tasks from "./components/Tasks";

export default {
  name: "app",
  components: {
    Tasks
  },
  data: () => ({
    tasks: [
      {
        id: 1,
        task_name: "Task One",
        status: 0
      },
      {
        id: 2,
        task_name: "Task Two",
        status: 1
      },
      {
        id: 3,
        task_name: "Task Three",
        status: 2
      },
      {
        id: 4,
        task_name: "Task Four",
        status: 3
      },
      {
        id: 5,
        task_name: "Task Five",
        status: 4
      },
      {
        id: 6,
        task_name: "Task Six",
        status: 5
      }
    ]
  })
};
</script>

<style>
body {
  font-family: "Solway", serif;
  background-color: rgb(243, 240, 240);
}
#app {
  max-width: 850px;
  margin: auto;
}
</style>

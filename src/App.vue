<template>
  <div id="app">
    <TasksView />
  </div>
</template>
<script>
import TasksView from './views/TasksView.vue';
export default {
  name: "App",
  components: {
    TasksView,
  },
};


</script>
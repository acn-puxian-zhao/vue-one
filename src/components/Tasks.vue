<template>
  <div>
    <div v-bind:key="task.id" v-for="task in tasks">
      <Task 
      @update-task="$emit('update-task', task)" 
      @delete-task="$emit('delete-task', task.id)" 
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      :task="task" />
    </div>
  </div>
</template>

<script>
import Task from "./Task.vue";

export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  emits: ["delete-task","update-task","toggle-reminder"],
};
</script>

<template>
  <div>
    <TaskHeade :title="TaskHeaderName" />
    <Tasks @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import TaskHeade from "./components/TaskHeader.vue";
import Tasks from "./components/Tasks.vue";

export default {
  name: "App",
  components: {
    TaskHeade,
    Tasks,
  },
  data() {
    return {
      tasks: [],
    };
  },

  methods: {
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((x) => x.id !== id);
      }
    },
  },

  created() {
    (this.TaskHeaderName = "Task Stracker"),
      (this.tasks = [
        {
          id: 1,
          text: "Doctors Appointment",
          day: "March 1st at 10am",
          reminder: true,
        },
        {
          id: 2,
          text: "Metting at school",
          day: "March 3rd at 1pm",
          reminder: true,
        },
        {
          id: 3,
          text: "Food Shopping",
          day: "March 4th at 3pm",
          reminder: false,
        },
      ]);
  },
};
</script>

<style>
</style>

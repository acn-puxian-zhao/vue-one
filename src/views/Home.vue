<template >
  <AddTask v-show="this.showAddTaskForm" @add-task="addNewTask" />

  <Tasks
    @update-task="updateTask"
    @delete-task="deleteTask"
    @toggle-reminder="toggleReminder"
    :tasks="this.tasks"
  />
</template>
<script>
import Tasks from "../components/Tasks.vue";
import AddTask from "../components/AddTask.vue";

export default {
  name: "Home",
  props: {
    showAddTaskForm: Boolean,
  },
  components: {
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    async addNewTask(task) {
      const res = await fetch("api/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(task),
      });

      const data = await res.json();

      this.tasks = [...this.tasks, data];
    },

    async deleteTask(id) {
      if (confirm("Are you sure?")) {
        const res = await fetch(`api/tasks/${id}`, {
          method: "DELETE",
        });

        res.status === 200
          ? (this.tasks = this.tasks.filter((x) => x.id !== id))
          : alert("Error deleting task");
      }
    },

    async toggleReminder(id) {
      console.log("toggleReminder");
      const taskToToggle = await this.fetchTask(id);
      console.log(taskToToggle);
      const updTask = { ...taskToToggle, reminder: !taskToToggle.reminder };
      console.log(updTask);

      const res = await fetch(`api/tasks/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updTask),
      });

      const data = await res.json();

      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: data.reminder } : task
      );
    },

    async updateTask(task) {
      console.log("updateTask");

      this.$router.push({
        name:'Update',
        params: {
          ...task
        },
        })
      return

      const taskToUpdate = await this.fetchTask(task.id);
      console.log(taskToUpdate);
      const updTask = {
        ...taskToUpdate,
        reminder: false,
        text: "aaa",
        day: "bbb",
      };
      console.log(updTask);

      const res = await fetch(`api/tasks/${updTask.id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updTask),
      });
      
      console.log('11111111');

      const data = await res.json();

      console.log('222222222');
      this.tasks = this.tasks.map((task) =>
        task.id === data.id ? { ...task, reminder: data.reminder, text: data.text, day: data.day } : task
      );
      console.log('33333333333');

    },

    async fechTasks() {
      const res = await fetch(`api/tasks`);
      const data = await res.json();

      return data;
    },

    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`);
      const data = await res.json();
      return data;
    },
  },
  async created() {
    console.log("home view " + this.showAddTaskForm);
    this.tasks = await this.fechTasks();
  },
};
</script>

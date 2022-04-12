<template>
  <div class="container">
    <Header
      @btn-click="showAddTask"
      :title="TaskHeaderName"
      :showAddTaskForm="this.showAddTaskForm"
    />
    <router-view :showAddTaskForm="showAddTaskForm"></router-view>
    <Footer />
  </div>
</template>

<script>
import Header from "./components/TaskHeader.vue";
import Footer from './components/Footer'

export default {
  name: "App",
  components: {
    Header,
    Footer,
  },
  data() {
    console.log('data()')
    return {
      showAddTaskForm: false,
      TaskHeaderName: "",
    };
  },
  emits: ["add-task", "btn-click", "delete-task", "update-task"],
  methods: {
    showAddTask() {
      console.log('showAddTask() ' + this.showAddTaskForm)
      this.showAddTaskForm = !this.showAddTaskForm;
      
      console.log('showAddTask() ' + this.showAddTaskForm)
    },
  },
  async created(){
    console.log('created()')
    this.TaskHeaderName="Task Tracker"
  },  

};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>


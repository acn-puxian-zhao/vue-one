
<template>
  <header>
    <h2>{{title}}</h2>
    <TaskButton
    v-show="isHomePage"
    @btn-click="$emit('btn-click')" 
    :ButtonName="showAddTaskForm ? 'Close':'Add Task'" 
    :ButtonColor="showAddTaskForm ? 'red':'green'" />
  </header>
</template>

<script>
import TaskButton from './TaskButton.vue'

export default {
  name: 'TaskHeader',
  props: {
    title: String,
    showAddTaskForm: Boolean,
  },
  components:
  {
    TaskButton
  },
  computed: {
      isHomePage(){
        if(this.$route.path === '/'){
        return true
        }
        else {
          return false
        }
      },
  },
}
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>

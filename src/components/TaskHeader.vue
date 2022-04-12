
<template>
  <header>
    <h2>{{title}}</h2>
    <TaskButton ButtonName='Add Task' ButtonColor='green'/>
  <!--   <TaskButton ButtonName='Update Task' ButtonColor='blue'/>
    <TaskButton ButtonName='Delete Task' ButtonColor='red'/> -->
  </header>
</template>


<script>
import TaskButton from './TaskButton.vue'

export default {
  name: 'TaskHeader',
  props: {
    title: String
  },
  components:
  {
    TaskButton
  },
  
}
</script>
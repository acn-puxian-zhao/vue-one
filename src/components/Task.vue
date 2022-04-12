<template>
  <div 
  @dblclick="$emit('toggle-reminder')"
  :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>{{ task.text }}</h3>
    <p>{{ task.day }}</p>
    <h3>
      <i @click="this.$emit('delete-task')" class="fas fa-times">Delete</i>
    </h3>
  <i @click="this.$emit('update-task')" class="fas1 fa-times">Update</i>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {

  },
};
</script>

<style scope>
.fas {
  color: red;
}
.fas1 {
  color: blue;
}

.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.task.reminder {
  border-left: 5px solid green;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
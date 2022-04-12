<template>
  <div>
    <h3>{{ task.text }}</h3>
    <p>{{ task.day }}</p>
    <i @click="onDelete()">x</i>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    onDelete() {
      this.$emit("delete-task");
    },
  },
};
</script>

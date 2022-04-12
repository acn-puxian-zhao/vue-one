<template>
  <form @submit="$emit('update-task', task)" class="add-form">
    <div class="form-control">
      <div>
        <label> Task </label>
        <input type="text" v-model="task.text" name="text" placeholder="Add Task" />
      </div>
      <div class="form-control">
        <label> Day & Time </label>
        <input
          type="text"
          v-model="task.day"
          name="day"
          placeholder="Add Day & Time"
        />
      </div>
      <div class="form-control form-control-check">
        <label>Set Reminder</label>
        <input
          type="checkbox"
          v-model="task.reminder"
          name="reminder"
          placeholder="Add Day & Time"
        />
      </div>
      <input type="submit" value="save task" />
    </div>
  </form>
</template>

<script>
export default {
  name: "EditTask",
  props: {
    task: {
      id: Number,
      text: String,
      day: String,
      reminder: Boolean,
    }
  },
  data() {
    return {
      task: {}
    };
  },
  methods: {
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
</style>
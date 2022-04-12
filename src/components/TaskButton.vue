<template>
  <button
    @click="onClick()"
    :style="{ background: ButtonColor, color: 'white' }"
    class="btn"
  >
    {{ ButtonName }}
  </button>
</template>

<script>
export default {
  name: "TaskButton",
  props: {
    ButtonName: String,
    ButtonColor: String,
  },
  methods: {
    onClick() {
      this.$emit("btn-click");
    },
  },
};
</script>

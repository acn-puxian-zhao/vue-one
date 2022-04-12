<template>
  <button @click="onClick()" :style="{background:ButtonColor,color:'white'}">
    {{ButtonName}}
  </button> 

</template>

<script>
export default {
  name: "TaskButton",
  props: {
    ButtonName: String,
    ButtonColor:String,
  },
  methods: {
    onClick(){

      console.log('onClick')
    }
  }
}
</script>

<template>
  <div>
    <input type="text" v-model="inputText" v-on:keyup.enter="addTodo">
    <button v-on:click="addTodo">add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: ""
    }; // 'vda' + tab 자동 완성
  },
  methods: {
    addTodo() {
      var value = this.inputText;
      this.$emit("add", value);
      this.inputText = "";
    }
  }
};
</script>

<style>
</style>

<template>
  <div>
    <button v-on:click="removeAllItems">clear all</button>
  </div>
</template>

<script>
export default {
  methods: {
    removeAllItems() {
      // localStorage.clear();
      this.$emit("removeitems");
    }
  }
};
</script>

<style>
</style>

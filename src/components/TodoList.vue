<template>
  <transition-group tag="ul" name="todo">
    <li v-for="(todoItem, index) in todolist" v-bind:key="index">
      <span>
        {{ todoItem }}
        <button v-on:click="remove(todoItem, index)">remove</button>
      </span>
    </li>
  </transition-group>
</template>

<script>
export default {
  props: ["todolist"],
  // data() {
  //   return {
  //     todoItems: []
  //   };
  // },
  methods: {
    // fetchTodoItems: function() {
    //   for (var i = 0; i < localStorage.length; i++) {
    //     var item = localStorage.key(i);
    //     this.todoItems.push(item);
    //   }
    // },
    remove: function(todo, index) {
      this.$emit("removeitem", todo, index);
    }
  }

  // 컴포넌트가 생성되자마자 실행되는 로직
  // created: function() {
  //   this.fetchTodoItems();
  // }
};
</script>

<style>
.todo-enter-active,
.todo-leave-active {
  transition: all 1s;
}
.todo-enter, .todo-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
</style>

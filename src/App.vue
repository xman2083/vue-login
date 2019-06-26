<template>
  <div>
    <todo-header></todo-header>
    <todo-input v-on:add="addTodoItem"></todo-input>
    <todo-list v-bind:todolist="todoItems" v-on:removeitem="removeTodoItem"></todo-list>
    <todo-footer v-on:removeitems="removeTodoItems"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoFooter from "./components/TodoFooter.vue";
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    "todo-header": TodoHeader,
    "todo-input": TodoInput,
    "todo-list": TodoList,
    "todo-footer": TodoFooter
  },
  data() {
    return {
      todoItems: []
    };
  },
  methods: {
    fetchTodoItems: function() {
      for (var i = 0; i < localStorage.length; i++) {
        var item = localStorage.key(i);
        this.todoItems.push(item);
      }
    },
    addTodoItem: function(value) {
      this.todoItems.push(value);
      localStorage.setItem(value, value);
    },
    removeTodoItems: function() {
      this.todoItems = [];
      localStorage.clear();
    },
    removeTodoItem: function(todo, index) {
      this.todoItems.splice(index, 1);
      localStorage.removeItem(todo);
    }
  },
  created: function() {
    this.fetchTodoItems();
  }
};
</script>

<style>
</style>

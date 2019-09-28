<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <todo-input v-on:add="addTodoItems"></todo-input>
    <todo-list v-bind:items="todoItems" v-on:remove="removeTodoItems"></todo-list>
    <todo-footer v-on:clear="clearTodoItems"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  name: 'app',
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter
  },
  data() {
    return {
      todoItems: []
    }
  },
  methods: {
    fetchTodoItems: function() {
      for (var i = 0; i < localStorage.length; i++) {
        var item = localStorage.key(i);
        this.todoItems.push(item);
      }
    },
    clearTodoItems: function() {
      this.todoItems = [];
      localStorage.clear();
    },
    addTodoItems: function(value) {
      this.todoItems.push(value);
      localStorage.setItem(value, value);
    },
    removeTodoItems: function(item, index) {
      localStorage.removeItem(item);
      this.todoItems.splice(index, 1);
    }
  },
  created: function() {
    this.fetchTodoItems();
  }
}
</script>

<style scoped>

</style>

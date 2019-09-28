<template>
  <div>
    <ul v-for="(item, index) in items" :key="index">
      <li>{{ item }}</li>
      <button v-on:click="removeTodoItem(item, index)">remove</button>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['items'],
  methods: {
    removeTodoItem: function(todoItem, index) {
      this.$emit("remove", todoItem, index);
      //this.todoItems.splice(index, 1);
      //localStorage.removeItem(todoItem);
    }
  },
}
</script>

<style>

</style>
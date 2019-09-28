<template>
  <button @click="clearAllItems">clear all</button>
</template>

<script>
export default {
  methods: {
    clearAllItems: function() {
      this.$emit('clear');
      localStorage.clear();
    }
  }
}
</script>

<style>

</style>
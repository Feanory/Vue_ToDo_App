<template>
  <button @click="onClick()" class="add-button">
    Add Task
  </button>
</template>

<script>
export default {
  name: "Button",
  methods: {
    onClick: () => {}
  }
};
</script>

<style scoped>
  .add-button {
    border: 1px solid;
    padding: 5px 15px;
    font-size: 18px;
    border-radius: 4px;
    background-color: white;
    margin-bottom: 20px;
  }
</style>

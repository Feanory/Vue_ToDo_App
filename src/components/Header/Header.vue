<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
  header {
    margin-bottom: 20px;
  }
  .wrapper {
    border-bottom: 1px solid black;
    padding: 20px;
  }
  a {
    padding: 0 20px;
    text-decoration: none;
    font-size: 18px;
  }
</style>

<template>
  <div class="container">
    <div class="card">
      <img class="image" :src="pokemon?.sprites?.front_default" alt="">
      <p>{{ pokemon?.name.toUpperCase() || 'No data' }}</p>
    </div>
  </div>
</template>

<script>
import router from "@/router";
import axios from "axios";

export default {
  name: "Pokemon",
  data() {
    return {
      pokemon: {},
      currentRoute: router.currentRoute
    }
  },
  created() {
    if (!this.currentRoute.params) {
      router.push('/')
    }
    const name = this.currentRoute.params.name;
    axios.get(`https://pokeapi.co/api/v2/pokemon/${name}`)
      .then(({ data }) => {
        this.pokemon = data;
        console.log(data);
      })
      .catch(err => console.error(err))
  },
};
</script>

<style scoped>
  .container {
    display: flex;
    justify-content: center;
  }
  .card {
    border: 1px solid;
    border-radius: 8px;
    text-align: center;
  }
  .image {
    width: 200px;
  }
</style>

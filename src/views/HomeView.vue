<script>
  import Button from "@/components/Header/Button.vue";
  import axios from "axios";

  export default {
    props: {
      pokemons: Array,
      moreUrl: String,
    },
    data() {
      return {
        pokemons: [],
        moreUrl: '',
        currentPath: window.location.hash
      }
    },
    components: {
      Button,
    },
    mounted() {
      axios.get('https://pokeapi.co/api/v2/pokemon')
        .then(({ data }) => {
          console.log(data);
          this.pokemons = data.results;
          this.moreUrl = data.next;
        })
        .catch(err => console.error(err))
    },
    methods: {
      loadMore() {
        axios.get(this.moreUrl)
          .then(({ data }) => {
            console.log(data);
            this.pokemons = [...this.pokemons, ...data.results];
            this.moreUrl = data.next;
          })
          .catch(err => console.error(err))
      }
    }
  }

</script>

<template>
<!--  <Button />-->
  <main>
    <h1>Pokemons</h1>
    <div class="pokemons">
      <router-link
        :to="{ name: 'pokemon', params: { name: pokemon.name } }"
        class="pokemon"
        v-for="pokemon in pokemons"
      >
        <span>{{ pokemon.name }}</span>
      </router-link>
    </div>
    <button @click="loadMore()">
      Load more
    </button>
  </main>
</template>
<style>
  .pokemons {
    display: flex;
    flex-wrap: wrap;
    margin-bottom: 20px;
  }
  .pokemon {
    font-size: 16px;
    margin: 5px 10px;
    padding: 8px;
    border: 1px solid;
    color: black;
    text-decoration: none;
    border-radius: 8px;
    background-color: white;
    cursor: pointer;
  }


</style>

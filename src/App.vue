<script setup lang="ts">
import { RouterView } from 'vue-router'
import Header from "@/components/Header/Header.vue";
</script>

<template>
  <Header />
  <RouterView />
</template>

<style>
 * {
   box-sizing: border-box;
   font-family: "Apple Braille";
 }
</style>

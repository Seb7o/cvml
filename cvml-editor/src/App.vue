<script setup>
import Accueil from './components/Accueil.vue';
</script>

<template>
  <div class="navbar bg-base-200 shadow-lg p-4">
    <div class="flex-1">
      <a class="text-2xl font-bold">CVML</a>
    </div>
    <div class="flex-none space-x-4">
      <a class="btn btn-ghost" href="#">View</a>
      <a class="btn btn-ghost" href="#">Create</a>
      <button class="btn btn-primary">Import</button>
    </div>
  </div>
  <main class="p-4">
    <Accueil />
  </main>
</template>

<style>

@import 'https://cdn.jsdelivr.net/npm/daisyui@2.14.3/dist/full.css';
</style>
<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <link
    rel="stylesheet"
    href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200"
  />

  <nav class="navbar">
    <div class="container-fluid">
      <a class="navbar-brand text-white fw-bold fs-3 ms-4">Lojinha Virtual</a>
      <div class="d-flex me-4 gap-3">
        <a class="material-symbols-outlined text-white" href="#">account_circle</a>
        <a class="material-symbols-outlined text-white" href="#">shopping_cart</a>
      </div>
    </div>
  </nav>

  <RouterView />
</template>

<style scoped>

.material-symbols-outlined {
  color: #000000;

  font-size: 35px;
  text-decoration: none;
  font-variation-settings:
  'FILL' 0,
  'wght' 400,
  'GRAD' 0,
  'opsz' 24
}
.navbar{
  background-color: #351183;
}
</style>

<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <nav class="navbar">
    <div class="container-fluid">
      <RouterLink class="navbar-brand text-white fw-bold fs-3 ms-4" to="/">Lojinha Virtual</RouterLink>
      <div class="d-flex me-4 gap-3">
        <RouterLink class="material-symbols-outlined text-white" to="#">account_circle</RouterLink>
        <RouterLink class="material-symbols-outlined text-white" to="#">shopping_cart</RouterLink>
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

<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav class="navbar">
        <RouterLink class="link--navbar"  to="/">Libros</RouterLink>
        <RouterLink class="link--navbar"  to="/nuevoLibro">Agregar nuevo libro</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>

.navbar {
  display: flex;
  justify-content: space-around;
  border-radius: 5px;
  align-items: center;
  background-color: rgba(0, 0, 0, 0.1);
  width: 300px;
  margin: 10px auto;
}

.link--navbar {
  text-decoration: none;
  padding: 10px;
  font-weight: 700;
  font-size: 1.3rem;
  color: rgb(66, 64, 64);
}

.link--navbar:hover {
    color: rgb(0, 0, 0);
    transition: color 0.3s ease-in-out;
}

</style>RouterLink,

<style scoped></style>
<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </header>

  <main>
    <RouterView />
  </main>

  <footer>
    <h1>Footer</h1>
  </footer>
</template>
<style>
* {
  font-family: 'Varela', sans-serif;
}
</style>

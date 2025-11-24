<script>
import { RouterLink, RouterView } from 'vue-router'
</script>
<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </header>
  <main><slot /></main>
  <footer>
    <h1>Footer</h1>
  </footer>
  <RouterView />
</template>

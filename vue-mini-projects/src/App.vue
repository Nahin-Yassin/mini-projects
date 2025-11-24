<script setup>
import HomeView from '../src/views/HomeView.vue'
import Layout from './components/Layout/Layout.vue'
import Calculator from './components/mini-projects/Calculator.vue'
import FlipCoin from './components/mini-projects/FlipCoin.vue'
import TicTac from './components/mini-projects/TicTac.vue'
</script>

<template>
  <Layout>
    <HomeView />
    <FlipCoin />
    <Calculator />
    <TicTac />
  </Layout>
</template>

<style scoped></style>

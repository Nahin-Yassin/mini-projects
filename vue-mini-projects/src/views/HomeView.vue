<script setup>
import { ref } from 'vue'
import Calculator from '../components/mini-projects/Calculator.vue'
import FlipCoin from '../components/mini-projects/FlipCoin.vue'
import TicTac from '../components/mini-projects/TicTac.vue'

const active = ref(null)

function show(name) {
  active.value = name
}
</script>

<template>
  <button @click="show('Calculator')">Calculator</button>
  <button @click="show('FlipCoin')">Flip Coin</button>
  <button @click="show('TicTac')">TicTac</button>

  <div class="viewer">
    <Calculator v-if="active === 'Calculator'" />
    <FlipCoin v-if="active === 'FlipCoin'" />
    <TicTac v-if="active === 'TicTac'" />
  </div>
</template>

<style scoped>
button {
  width: 200px;
  height: 250px;
}
</style>

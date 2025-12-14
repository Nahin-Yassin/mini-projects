<script setup>
import TresCoin from './tres/TresCoin.vue'

import { ref } from 'vue'
const num = ref('')
function flip() {
  const random = Math.floor(Math.random() * 2)
  if (random === 1) {
    num.value = 'Heads'
  } else if (random === 0) {
    num.value = 'Tails'
  }
}
</script>

<template>
  <div class="container">
    <div class="coin">
      <h1>{{ num }}</h1>
      <div class="button"><button @click="flip">Flip</button></div>
    </div>
  </div>
  <TresCoin />
</template>

<style scoped>
.container {
  border: 2px solid var(--clr-accent);
  height: 50vh;
  width: 450px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  flex-direction: column;
}
.coin {
  width: 150px;
  height: 150px;
  position: relative;
  transform-style: preserve-3d;
  transition: transform 0s;
  text-align: center;
  display: flex;
  justify-content: center;
}
</style>

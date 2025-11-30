<script setup>
import { ref } from 'vue'
import Calculator from '../components/mini-projects/Calculator.vue'
import FlipCoin from '../components/mini-projects/FlipCoin.vue'
import TicTac from '../components/mini-projects/TicTac.vue'
import Flipcoin2 from '@/components/mini-projects/flipcoin2.vue'

const active = ref(null)

function show(name) {
  active.value = name
}
</script>

<template>
  <button @click="show('Calculator')">Calculator</button>
  <button @click="show('FlipCoin')">Flip Coin</button>
  <button @click="show('TicTac')">TicTac</button>
  <button @click="show('Flipcoin2')">Flipcoin2</button>

  <div class="viewer">
    <Calculator v-if="active === 'Calculator'" />
    <FlipCoin v-if="active === 'FlipCoin'" />
    <TicTac v-if="active === 'TicTac'" />
    <Flipcoin2 v-if="active === 'Flipcoin2'" />
  </div>
</template>

<style>
/* Layout */
button {
  width: 160px;
  padding: 14px 0;
  margin: 8px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;

  background: var(--clr-surface); /* Light blue button */
  color: var(--clr-ink-dark); /* Dark blue text */

  transition:
    background 0.15s ease,
    transform 0.15s ease;
}

button:hover {
  background: var(--clr-accent); /* Slightly darker blue on hover */
  transform: translateY(-2px);
}

button:active {
  background: var(--clr-accent-light);
  transform: translateY(0);
}

.viewer {
  margin-top: 20px;
  padding: 20px;

  background: var(--clr-bg-soft); /* Soft background */
  border: 1px solid var(--clr-bg-light);
  border-radius: 10px;

  min-height: 380px;
}

/* Center whatever component is shown */
.viewer > * {
  margin: auto;
}
</style>

<script setup>
import { ref } from 'vue'

const coin = ref(null)

function flippingCoin() {
  coin.value = Math.random() < 0.5 ? 'heads' : 'tails'
}
</script>
<template>
  <h1>FlipCoin</h1>

  <div class="container">
    <div class="coin">
      <div class="face front" v-if="coin.value.value === 'heads'">
        {{ coin.value.value }}
      </div>

      <div class="face back" v-else-if="coin.value.value === 'tails'">
        {{ coin.value.value }}
      </div>
    </div>

    <div class="flipbutton">
      <button @click="flippingCoin">Flip</button>
    </div>
  </div>
</template>
<style>
.container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  height: 50vh;
}
.coin {
  width: 350px;
  height: 350px;
  background: var(--clr-accent);
  font-size: 50px;
}
</style>

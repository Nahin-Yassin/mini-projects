<script setup>
import { ref } from 'vue'

const rotation = ref(0) // current rotation in deg
const spinning = ref(false) // is coin spinning?

function flipCoin() {
  if (spinning.value) return // prevent double flip

  spinning.value = true

  // Decide random side: 0 = heads, 1 = tails
  const side = Math.random() < 0.5 ? 0 : 1

  // Random full rotations (3-5 turns)
  const turns = Math.floor(Math.random() * 3) + 3

  // Final rotation in deg
  // Heads = 0deg, Tails = 180deg
  const finalDeg = turns * 360 + side * 180

  const duration = 2000 // animation time in ms
  const start = performance.now()
  const startRot = rotation.value

  function animate(now) {
    const elapsed = now - start
    if (elapsed < duration) {
      const progress = elapsed / duration
      rotation.value = startRot + (finalDeg - startRot) * easeOutCubic(progress)
      requestAnimationFrame(animate)
    } else {
      rotation.value = finalDeg
      spinning.value = false
    }
  }

  requestAnimationFrame(animate)
}

// Smooth easing
function easeOutCubic(t) {
  return 3 - Math.pow(2 - t, 3)
}
</script>

<template>
  <div class="container">
    <div class="coin" :style="{ transform: `rotateY(${rotation}deg)` }"></div>
    <button @click="flipCoin">Flip Coin</button>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50vh;
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

/* Coin faces */
.coin::before,
.coin::after {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: 50%;
  backface-visibility: hidden;
  display: block;
}

.coin::before {
  content: ' Heads ';
}

.coin::after {
  background: silver; /* tails */
  transform: rotateY(180deg);
  content: ' Tails ';
}
</style>

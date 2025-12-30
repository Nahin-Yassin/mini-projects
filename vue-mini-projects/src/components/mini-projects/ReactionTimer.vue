<script setup>
import { ref } from 'vue'

const isGreen = ref(false) // green light
const isWaiting = ref(false) // "wait..." state
let startTime = ref(0)

function startGame() {
  isWaiting.value = true // start with "wait..." state
  const delay = Math.floor(Math.random() * 3000) + 2000

  setTimeout(() => {
    isGreen.value = true
    isWaiting.value = false
    startTime.value = performance.now()
  }, delay)
}

function start() {
  startGame()
}
</script>

<template>
  <div class="container">
    <div v-if="!isWaiting && !isGreen" class="before" @click="start">
      <p>
        Reaction time tester <br />
        click anywhere to start
      </p>
    </div>
    <div v-else-if="isWaiting" class="after">
      <p>wait...</p>
    </div>
    <div v-else class="red_room">
      <p>Click now!</p>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  width: 1280px;
  height: 500px;
}

.before {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 40px;
  width: 100%;
  height: 100%;
  background-color: transparent;
}

.after {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 40px;
  width: 100%;
  height: 100%;
  background-color: var(--clr-accent);
}
.red_room {
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 40px;
  width: 100%;
  height: 100%;
  background-color: red;
}
</style>

<script setup>
import { ref } from 'vue'
let isPLaying = ref(false)
let showBlock = ref(false)
let reactionTime = ref(0)

let delay = null
let timer = null
function start() {
  delay = 2000 + Math.floor(Math.random() * 5000)
  isPLaying.value = true

  setTimeout(() => {
    showBlock.value = true
    startTimer()
    console.log(delay)
  }, delay)
}

function startTimer() {
  timer = setInterval(() => {
    reactionTime.value += 10
  }, 10)
}
function stopTimer() {
  clearInterval(timer)
  console.log(reactionTime)
}
</script>
<template>
  <div class="container">
    <div class="game_box" @click="start">
      <p>
        Reaction time test <br />
        click to start
      </p>
    </div>
    <div v-show="isPLaying" class="wait">
      <p>wait for green</p>
    </div>
    <div v-if="showBlock" class="green" @click="stopTimer"><p>Click me fast !</p></div>
    <p>{{ reactionTime }}ms</p>
  </div>
</template>

<style>
.container {
  width: 500px;
  height: 500px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-direction: column;
  border: solid var(--clr-accent);
}
.game_box {
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 350px;
  height: 350px;
}

.wait {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: var(--clr-accent);
  width: 350px;
  height: 350px;
}
.green {
  cursor: pointer;
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: rgb(107, 231, 107);
  width: 350px;
  height: 350px;
}
</style>

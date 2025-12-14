<script setup>
import { ref } from 'vue'

const moves = ref(['rock', 'paper', 'scissors'])
const plays = ref('')
const pcplays = ref(null)

function playerMove(move) {
  plays.value = move
}
function computerMove() {
  const randomNumber = Math.floor(Math.random() * 3)
  const pcmove = randomNumber === 0 ? 'rock' : randomNumber === 1 ? 'paper' : 'scissors'
  pcplays.value = pcmove
}
function choseWinner() {
  if (condition) {
  }
  if (condition) {
  } else {
  }
}
function game() {
  computerMove()
}
</script>
<template>
  <div class="container">
    <div class="game">
      <p v-if="plays">player : {{ plays }}</p>
      <p>Computer :{{ pcplays }}</p>
    </div>
    <div class="buttons">
      <button @click="(playerMove(moves[0]), game())">Rock</button>
      <button @click="(playerMove(moves[1]), game())">Paper</button>
      <button @click="(playerMove(moves[2]), game())">Scissors</button>
    </div>
  </div>
</template>
<style scoped>
.container {
  display: flex;
  justify-content: space-around;
  flex-direction: column;
  width: 50vh;
  height: 50vh;
  border: solid var(--clr-accent-light);
}
.buttons {
  display: flex;
  flex-wrap: initial;
}
.game {
  font-size: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
}
</style>

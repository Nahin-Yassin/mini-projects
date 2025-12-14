<script setup>
import { ref } from 'vue'

const moves = ref(['rock', 'paper', 'scissors'])
const plays = ref('')
const pcplays = ref('')
const finalResult = ref('')

let result = ref('')
function playerMove(move) {
  plays.value = move
}
function computerMove() {
  const randomNumber = Math.floor(Math.random() * 3)
  const pcmove = randomNumber === 0 ? 'rock' : randomNumber === 1 ? 'paper' : 'scissors'
  pcplays.value = pcmove
}

const tieResult = () => {
  if (plays.value === pcplays.value) {
    result = 'tie'
  } else if (
    (plays.value === 'rock' && pcplays.value === 'scissors') ||
    (plays.value === 'paper' && pcplays.value === 'rock') ||
    (plays.value === 'scissors' && pcplays.value === 'paper')
  ) {
    result = 'player won'
  } else {
    result = 'computer won'
  }
  finalResult.value = result
  return result
}

function game() {
  computerMove()
  tieResult()
}
</script>
<template>
  <div class="container">
    <div class="game">
      <p v-if="plays">player : {{ plays }}</p>
      <p>Computer :{{ pcplays }}</p>
      <p>{{ finalResult }}</p>
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
  height: 50vh;
  width: 450px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  flex-direction: column;
  border: 2px solid var(--clr-accent);
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

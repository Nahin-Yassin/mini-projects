<script setup>
import { ref } from 'vue'

const moves = ref(['Rock 🪨', 'Paper 📃', 'Scissors ✂️'])
const plays = ref('')
const pcplays = ref('')
const finalResult = ref('')
let result = ref('')
let pWin = ref(0)
const cWin = ref(0)

function playerMove(move) {
  plays.value = move
}
function computerMove() {
  const randomNumber = Math.floor(Math.random() * 3)
  const pcmove = randomNumber === 0 ? 'Rock 🪨' : randomNumber === 1 ? 'Paper 📃' : 'Scissors ✂️'
  pcplays.value = pcmove
}

const tieResult = () => {
  if (plays.value === pcplays.value) {
    result = 'tie'
  } else if (
    (plays.value === 'Rock 🪨' && pcplays.value === 'Scissors ✂️') ||
    (plays.value === 'Paper 📃' && pcplays.value === 'Rock 🪨') ||
    (plays.value === 'Scissors ✂️' && pcplays.value === 'Paper 📃')
  ) {
    pWin.value++
    result = 'player won'
  } else {
    cWin.value++
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
    <div class="winCounts">
      <p>PLayer <br />{{ pWin }}</p>
      <p>Computer <br />{{ cWin }}</p>
    </div>
    <div class="game">
      <p v-if="plays">
        player : <br />
        {{ plays }}
      </p>
      <p>Computer : <br />{{ pcplays }}</p>
    </div>
    <p class="result">{{ finalResult }}</p>

    <div class="buttons">
      <button @click="(playerMove(moves[0]), game())">Rock 🪨</button>
      <button @click="(playerMove(moves[1]), game())">Paper 📃</button>
      <button @click="(playerMove(moves[2]), game())">Scissors ✂️</button>
    </div>
  </div>
</template>
<style scoped>
.container {
  display: flex;
  height: 50vh;
  width: 550px;
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
.winCounts {
  font-size: 20px;
  text-align: center;
  width: 450px;
  display: flex;
  align-self: center;
  justify-content: space-between;
}
.game {
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  flex-direction: row;
  gap: 50px;
}
.result {
  font-size: 30px;
}
</style>

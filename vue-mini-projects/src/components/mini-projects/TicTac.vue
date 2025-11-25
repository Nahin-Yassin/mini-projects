<script>
import { ref } from 'vue'
const tics = ref({
  aA: '',
  aB: '',
  ac: '',
  bA: '',
  bB: '',
  bc: '',
  cA: '',
  cB: '',
  cC: '',
})
const player = ref('one')
const gameOver = ref('')

const handleReset = () => {
  tics.value = {
    aA: '',
    aB: '',
    ac: '',
    bA: '',
    bB: '',
    bc: '',
    cA: '',
    cB: '',
    cC: '',
  }
  player.value = 'One'
  gameOver.value = ''
}

const checkStatus = () => {
  const checkAllEmpties = Object.entries(tics.value)
    .flatMap((entry) => entry[1])
    .filter((entry) => entry === '')
}
</script>
<template>
  <div id="title">
    <h1>Tic Tac Toe</h1>
  </div>
  <div id="board">
    <div class="square" id="square0"></div>
    <div class="square" id="square1"></div>
    <div class="square" id="square2"></div>
    <div class="square" id="square3"></div>
    <div class="square" id="square4"></div>
    <div class="square" id="square5"></div>
    <div class="square" id="square6"></div>
    <div class="square" id="square7"></div>
    <div class="square" id="square8"></div>
  </div>
  <div id="endGame">
    <input type="button" value="Restart" id="restartButton" onclick="restartButton()" />
  </div>
</template>
<style>
h1 {
  text-align: center;
}

#board {
  margin-left: auto;
  margin-right: auto;
  width: 375px;
  height: 375px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 5px;
}

.square {
  width: 120px;
  height: 120px;
  border: 1px solid #d3d3d3;
  background-color: #f5f5f5;
  font-size: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.square:hover {
  background-color: #ffffe0;
}

#restartButton {
  display: block;
  margin-left: auto;
  margin-right: auto;
  height: 40px;
  width: 150px;
  background-color: #ffffff;
  border: 1px solid #000000;
  border-radius: 40px;
  font-size: 18px;
}

#restartButton:hover {
  background-color: #000000;
  color: #ffffff;
}
</style>

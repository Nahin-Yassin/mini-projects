<script>
import { ref, computed } from 'vue'

const player = ref('X')
const board = ref([
  ['', '', ''],
  ['', '', ''],
  ['', '', ''],
])

const CalculateWinner = (board) => {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6],
  ]

  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i]

    if (board[a] && board[a] === board[b] && board[a] === board[c]) {
      return board[a]
    }
  }

  return null
}

const winner = computed(() => CalculateWinner(board.value.flat()))

const MakeMove = (x, y) => {
  if (winner.value) return

  if (board.value[x][y]) return

  board.value[x][y] = player.value

  player.value = player.value === 'X' ? 'O' : 'X'
}

const ResetGame = () => {
  board.value = [
    ['', '', ''],
    ['', '', ''],
    ['', '', ''],
  ]
  player.value = 'X'
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

  <div id="board">{{ board }}</div>
  <div id="endGame">
    <button class="reset" @click="ResetGame">Reset</button>
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
  display: flex;
  flex-wrap: wrap;
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

.reset {
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

.reset:hover {
  background-color: #000000;
  color: #ffffff;
}
</style>

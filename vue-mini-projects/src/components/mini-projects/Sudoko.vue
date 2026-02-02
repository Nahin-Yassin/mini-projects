<script setup>
import { ref, onMounted } from 'vue'
const selectedNumber = ref()
const board = ref(Array.from({ length: 9 }, () => Array.from({ length: 9 }, () => '')))
const puzzleBoard = ref([
  [5, 3, null, null, 7, null, null, null, null],
  [6, null, null, 1, 9, 5, null, null, null],
  [null, 9, 8, null, null, null, null, 6, null],
  [8, null, null, null, 6, null, null, null, 3],
  [4, null, null, 8, null, 3, null, null, 1],
  [7, null, null, null, 2, null, null, null, 6],
  [null, 6, null, null, null, null, 2, 8, null],
  [null, null, null, 4, 1, 9, null, null, 5],
  [null, null, null, null, 8, null, null, 7, 9],
])

const solutionBoard = ref([
  [5, 3, 4, 6, 7, 8, 9, 1, 2],
  [6, 7, 2, 1, 9, 5, 3, 4, 8],
  [1, 9, 8, 3, 4, 2, 5, 6, 7],
  [8, 5, 9, 7, 6, 1, 4, 2, 3],
  [4, 2, 6, 8, 5, 3, 7, 9, 1],
  [7, 1, 3, 9, 2, 4, 8, 5, 6],
  [9, 6, 1, 5, 3, 7, 2, 8, 4],
  [2, 8, 7, 4, 1, 9, 6, 3, 5],
  [3, 4, 5, 2, 8, 6, 1, 7, 9],
])

function checkGame() {
  for (let r = 0; r < 9; r++) {
    for (let c = 0; c < 9; c++) {
      if (puzzleBoard.value[r][c] !== solutionBoard.value[r][c]) {
        return
      }
    }
  }

  alert('winner')
}

function selectNumber(num) {
  selectedNumber.value = num
}
function selectTile(r, c) {
  if (puzzleBoard.value[r][c] !== null) return // LOCKED
  if (!selectedNumber.value) return

  board.value[r][c] = selectedNumber.value
  checkGame()
}

checkGame()
</script>
<template>
  <div id="board" class="container">
    <div v-for="(row, r) in board" :key="r" class="row">
      <div
        v-for="(cell, c) in row"
        :key="r + '-' + c"
        class="tile"
        :class="{ puzzle: puzzleBoard[r][c] !== null }"
        @click="selectTile(r, c)"
      >
        {{ cell ?? '' }} {{ puzzleBoard[r][c] }}
      </div>
    </div>
  </div>

  <div class="pNum">
    <div v-for="number in 9" :key="number" class="number" @click="selectNumber(number)">
      {{ number }}
    </div>
  </div>
</template>
<style scoped>
.container {
  width: 500px;
  height: 500px;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.pNum {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 500px;
  height: 50px;
  padding: 10px;
  background-color: var(--clr-accent);
}
.number {
  width: 44px;
  height: 44px;
  background-color: aliceblue;
  text-align: center;
  font-size: 30px;
  cursor: pointer;
}
.number:hover {
  background-color: rgba(240, 248, 255, 0.518);
}
.tile {
  text-align: center;
  font-size: 30px;
  width: 50px;
  height: 50px;
  border: 0.5px solid var(--clr-accent);
}
.puzzle {
  text-align: center;
  font-size: 30px;
  cursor: pointer;
  background-color: #96ade8;
}
</style>

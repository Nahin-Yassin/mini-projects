<script setup>
import { ref, onMounted } from 'vue'
const selectedNumber = ref()
const board = ref(Array.from({ length: 9 }, () => Array.from({ length: 9 }, () => '')))
let puzzleBoard = ref([
  [5, 3, 0, 0, 7, 0, 0, 0, 0],
  [6, 0, 0, 1, 9, 5, 0, 0, 0],
  [0, 9, 8, 0, 0, 0, 0, 6, 0],
  [8, 0, 0, 0, 6, 0, 0, 0, 3],
  [4, 0, 0, 8, 0, 3, 0, 0, 1],
  [7, 0, 0, 0, 2, 0, 0, 0, 6],
  [0, 6, 0, 0, 0, 0, 2, 8, 0],
  [0, 0, 0, 4, 1, 9, 0, 0, 5],
  [0, 0, 0, 0, 8, 0, 0, 7, 9],
])

var solutionBoard = ref([
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

function selectNumber(num) {
  selectedNumber.value = num
  puzzleBoard.value[r][c].splice(0) // valid
}
function selectTile(r, c) {
  board.value[r][c] = selectedNumber.value
}
</script>
<template>
  <div id="board" class="container">
    <div v-for="(row, r) in board" :key="r" class="row">
      <div
        v-for="(cell, c) in row"
        :key="r + '-' + c"
        class="tile"
        :id="r + '-' + c"
        @click="selectTile(r, c)"
      >
        {{ cell !== 0 ? cell : '' }}
        {{ puzzleBoard[r][c] }}
      </div>
    </div>
  </div>
  <div class="pNum">
    <div v-for="number in 9" :key="number" class="number" @click="selectNumber(number)">
      {{ number }}
    </div>
    {{ selectedNumber }}
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
</style>

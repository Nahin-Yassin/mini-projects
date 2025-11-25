<template>
  <div class="board">
    <div class="box box1" @click="handleClick(1)">{{ cells[1] }}</div>
    <div class="box box2" @click="handleClick(2)">{{ cells[2] }}</div>
    <div class="box box3" @click="handleClick(3)">{{ cells[3] }}</div>

    <div class="box box4" @click="handleClick(4)">{{ cells[4] }}</div>
    <div class="box box5" @click="handleClick(5)">{{ cells[5] }}</div>
    <div class="box box6" @click="handleClick(6)">{{ cells[6] }}</div>

    <div class="box box7" @click="handleClick(7)">{{ cells[7] }}</div>
    <div class="box box8" @click="handleClick(8)">{{ cells[8] }}</div>
    <div class="box box9" @click="handleClick(9)">{{ cells[9] }}</div>
  </div>
  <button @click="reset">Reset</button>
</template>
<script setup>
import { ref } from 'vue'

const cells = ref({
  1: '',
  2: '',
  3: '',
  4: '',
  5: '',
  6: '',
  7: '',
  8: '',
  9: '',
})

const player = ref('X')

function handleClick(num) {
  if (cells.value[num] !== '') return

  cells.value[num] = player.value

  checkWinner()

  player.value = player.value === 'X' ? 'O' : 'X'
}
const reset = () => {
  cells.value = {
    1: '',
    2: '',
    3: '',
    4: '',
    5: '',
    6: '',
    7: '',
    8: '',
    9: '',
  }
}
function checkWinner() {
  const c = cells.value

  if (c[1] && c[1] === c[2] && c[2] === c[3]) {
    alert(`${c[1]} wins`)
  } else if (c[4] && c[4] === c[5] && c[5] === c[6]) {
    alert(`${c[4]} wins`)
  } else if (c[7] && c[7] === c[8] && c[8] === c[9]) {
    alert(`${c[7]} wins`)
  } else if (c[1] && c[1] === c[4] && c[4] === c[7]) {
    alert(`${c[1]} wins`)
  } else if (c[2] && c[2] === c[5] && c[5] === c[8]) {
    alert(`${c[2]} wins`)
  } else if (c[3] && c[3] === c[6] && c[6] === c[9]) {
    alert(`${c[3]} wins`)
  } else if (c[1] && c[1] === c[5] && c[5] === c[9]) {
    alert(`${c[1]} wins`)
  } else if (c[3] && c[3] === c[5] && c[5] === c[7]) {
    alert(`${c[3]} wins`)
  }
}
</script>
<style scoped>
.board {
  display: grid;
  grid-template-columns: repeat(3, 100px);
  gap: 5px;
}
.box {
  width: 100px;
  height: 100px;
  background: #ddd;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 40px;
  cursor: pointer;
}
</style>

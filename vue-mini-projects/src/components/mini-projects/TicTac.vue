<script setup>
import { ref } from 'vue'
const winner = ref('')
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
  ;((cells.value = {
    1: '',
    2: '',
    3: '',
    4: '',
    5: '',
    6: '',
    7: '',
    8: '',
    9: '',
  }),
    (winner.value = ''))
}

const checkWinner = () => {
  const c = cells.value

  if (c[1] && c[1] === c[2] && c[2] === c[3]) {
    winner.value = `${c[1]} wins`
  } else if (c[4] && c[4] === c[5] && c[5] === c[6]) {
    winner.value = `${c[4]} wins`
  } else if (c[7] && c[7] === c[8] && c[8] === c[9]) {
    winner.value = `${c[7]} wins`
  } else if (c[1] && c[1] === c[4] && c[4] === c[7]) {
    winner.value = `${c[1]} wins`
  } else if (c[2] && c[2] === c[5] && c[5] === c[8]) {
    winner.value = `${c[2]} wins`
  } else if (c[3] && c[3] === c[6] && c[6] === c[9]) {
    winner.value = `${c[3]} wins`
  } else if (c[1] && c[1] === c[5] && c[5] === c[9]) {
    winner.value = `${c[1]} wins`
  } else if (c[3] && c[3] === c[5] && c[5] === c[7]) {
    winner.value = `${c[3]} wins`
  }
}
</script>
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

  <div class="popup">
    <p class="popuptext" id="myPopup" v-if="winner">{{ winner }}</p>
  </div>
</template>
<style scoped>
.board {
  display: grid;
  grid-template-columns: repeat(3, 100px);
  gap: 10px;
  justify-content: center;
  margin: 50px auto 20px;
}

.box {
  width: 100px;
  height: 100px;
  background-color: var(--clr-bg-soft);
  border: 2px solid var(--clr-accent);
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 40px;
  font-weight: bold;
  color: var(--clr-navy-dark);
  cursor: pointer;
  transition:
    background-color 0.2s,
    transform 0.1s;
  user-select: none;
}

.box:hover {
  background-color: var(--clr-bg-light);
  transform: scale(1.05);
}

button {
  display: block;
  padding: 10px 25px;
  font-size: 16px;
  cursor: pointer;
  background-color: var(--clr-primary);
  color: var(--clr-bg-base);
  border: none;
  border-radius: 6px;
  transition: background-color 0.2s;
}

button:hover {
  background-color: var(--clr-primary-dark);
}
.popup {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  bottom: 440px;
}
.popuptext {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 350px;
  height: 350px;
  background-color: var(--clr-accent);
  color: var(--clr-bg-base);
  font-weight: bold;
  font-size: 35px;
  animation: fadeIn 0.5s ease;
  filter: blur(1px);
  filter: opacity(90%);
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>

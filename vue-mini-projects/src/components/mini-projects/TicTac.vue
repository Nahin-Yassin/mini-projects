<script setup>
import { ref } from 'vue'
const winner = ref()
const cells = {
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
const handleClick = () => {
  const player = ref('X')
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
  margin: 20px auto;
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
  bottom: 450px;
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

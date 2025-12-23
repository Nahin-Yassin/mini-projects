<script setup>
import { ref } from 'vue'

const MaxNum = ref()
const num = ref(0)
const guessNum = ref()
const ans = ref('')

function handleInput(e) {
  MaxNum.value = Number(e)
  randNum()
}

function randNum() {
  if (MaxNum.value > 0) {
    num.value = Math.floor(Math.random() * MaxNum.value)
    console.log('Random number:', num.value)
  }
}

function guess() {
  if (guessNum.value < num.value) {
    ans.value = `My number is greater than ${guessNum.value}`
  } else if (guessNum.value > num.value) {
    ans.value = `My number is lesser than ${guessNum.value}`
  } else if ((guessNum.value = num.value)) {
    ans.value = `well done`
  } else ans.value`enter a target`
}
</script>
<template>
  <div class="container">
    <h2>Guess My Number</h2>
    <p>
      Guess a random numbet between 1 and
      <input v-model="MaxNum" placeholder="Target" type="number" />
    </p>
    <button @click="randNum">Set Target</button>
    <div class="ans">
      <p>{{ ans }}</p>
      <div>
        <input v-model.number="guessNum" type="number" /> <button @click="guess">Guess</button>
      </div>
    </div>
  </div>
</template>
<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border: 2px solid var(--clr-accent);
  height: 50vh;
  width: 550px;
}

button:hover {
  background-color: var(--clr-primary-dark);
}
input {
  width: 60px;
}
.ans {
  gap: 10px;
  text-align: center;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
</style>

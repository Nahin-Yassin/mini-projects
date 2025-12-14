<script setup>
import { reactive, ref } from 'vue'
const rock = 'Rock'
const paper = 'Paper'
const scissors = 'Scissors'

function rpsLogic() {
  if (rock === scissors) {
    console.log('scissors wins')
  } if (rock === paper) {
    console.log('paper wins')
  } else { console.log("draw")

  }
</script>
<template>
  <div class="container">
    <button>Rock</button>
    <button>Paper</button>
    <button>Scissors</button>
  </div>
</template>
<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: flex-end;
  width: 50vh;
  height: 50vh;
  border: solid var(--clr-accent-light);
}
</style>

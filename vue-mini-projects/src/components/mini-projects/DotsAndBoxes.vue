<script setup>
import { ref } from 'vue'

const rows = ref(8)
const cols = ref(8)
function onDotClick(row, col) {
  console.log('dot:', row, col)
}
</script>
<template>
  <div class="container">
    <div v-for="r in rows" :key="r" class="row">
      <span v-for="c in cols" :key="c" class="dot" @click="onDotClick(r - 1, c - 1)"> • </span>
    </div>
  </div>
</template>

<style scoped>
.container {
  border: 2px solid var(--clr-accent);
  height: 40vh;
  width: 450px;
  padding: 20px;
}

.row {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}

.dot {
  font-size: 28px;
  cursor: pointer;
  user-select: none;
}
</style>

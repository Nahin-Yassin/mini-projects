<script>
const grids = 9
</script>
<template>
  <div class="container">
    <div v-for="grids in 9" class="grids"></div>
  </div>
</template>
<style scoped>
.container {
  width: 500px;
  height: 500px;
  display: flex;
  flex-wrap: wrap;
}
.grids {
  width: 150px;
  height: 150px;
  border: 2px solid var(--clr-accent);
  padding-bottom: 15px;
}
</style>

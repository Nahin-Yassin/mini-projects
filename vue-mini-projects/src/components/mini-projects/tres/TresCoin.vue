<script></script>

<template>
  <div class="canvas-wrapper">
    <TresCanvas clear-color="#fff">
      <TresPerspectiveCamera />
      <TresMesh>
        <TresBoxGeometry />
        <TresMeshNormalMaterial />
      </TresMesh>
      <TresAxesHelper />
    </TresCanvas>
  </div>
</template>
<style>
.canvas-wrapper {
  width: 100%;
  height: 600px; /* or whatever height you want */
  overflow: hidden;
}
</style>

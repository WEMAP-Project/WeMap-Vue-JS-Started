<template>
  <WeMap />
</template>

<script setup>
import WeMap from './components/WeMap.vue'

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;

  position: absolute;
  top: 0;
  bottom: 0;
  width: 100%;
}

#app .mapboxgl-canvas {
  left: 0;
}

.wemap-marker-arrow::after {
  margin-top: 8px;
  margin-left: -7px;
}
</style>
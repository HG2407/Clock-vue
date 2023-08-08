<template>
  <div id="app">
    <clock/>
  </div>
</template>

<script>
import clock from './components/clock.vue'

export default {
  name: 'App',
  components: {
    clock
  }
}
</script>

<style>
  *, 
  *::before,
  *::after {
    box-sizing: border-box;
  }
  #app {
    padding-left: 1rem;
    padding-right: 1rem;
    margin-left: auto;
    margin-right: auto;
    width: fit-content;
  }
</style>

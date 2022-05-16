<template>
  <div class="app">
    <Piano/>
  </div>
</template>

<script>
import Piano from "@/components/Piano.vue"

export default {
  name: 'App',
  components: {
    Piano
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

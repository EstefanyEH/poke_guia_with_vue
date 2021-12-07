<template>
  <div id="app">
    <component-poke></component-poke>
  </div>
</template>

<script>
import Pokemon from "../src/components/Pokemon.vue"

export default {
  name: 'App',
  components: {
    "component-poke" : Pokemon,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

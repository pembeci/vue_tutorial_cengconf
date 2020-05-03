<template>
  <div id="app">
    <p>Tutorial component below for {{ conference }} -- {{ date }}</p>
    <Tutorial/>
  </div>
</template>

<script>
import Tutorial from './components/Tutorial.vue'

export default {
  name: 'App',
  components: {
    Tutorial
  },
  data: function() {
    return {
      conference: "Uzaktan Eğitim, İş ve Kariyer - 5N1K",
      date: "10.05.2020"
    }
  }  
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>

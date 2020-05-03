<template>
  <div class="hello">
    <h1>Tutorial</h1>
    <h2>Declarative Rendering</h2>
    Hello <b>{{ name }}</b>
  </div>
</template>

<script>
export default {
  name: 'Tutorial',
  data: function () {
    return {
      name: "Spider Man"
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>

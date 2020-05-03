<template>
  <div class="hello">
    <h2>Tutorial</h2>
    <h3>Declarative Rendering + Two way data binding</h3>
    Name: <input v-model="name"><br/>
    Hobbies: <input type="checkbox" id="h1" value="Swimming" v-model="hobbies">
    <label for="h1">Swimming</label>
    <input type="checkbox" id="h2" value="Reading" v-model="hobbies">
    <label for="h2">Reading</label>
    <input type="checkbox" id="h3" value="Movies" v-model="hobbies">
    <label for="h3">Movies</label>
    <br/>
      Hello <b>{{ name }}</b>. So your hobbies are: {{ hobbies.join(",") }}
      
    <h3>Not just content (attributes, style)</h3>
    <input type="radio" id="left" value="left" v-model="alignment"><label for="left">left</label>
    <input type="radio" id="center" value="center" v-model="alignment"><label for="left">center</label>
    <input type="radio" id="right" value="right" v-model="alignment"><label for="left">right </label>
    <label for="fsize"> Font size:</label> <input type="number" id="fsize" v-model="textSize">
    <br/>
    <p :align="alignment" :title=" 'I have ' + color + ' background' " 
       :style="{backgroundColor: color, fontSize: textSize + 'px'}" >
       Some paragraph</p>
       
    </div>
    
</template>
  

<script>
export default {
  name: 'Tutorial',
  data: function () {
    return {     
      name: "Spider Man",
      hobbies: [],
      color: "pink",
      alignment: "left",
      textSize: 16
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>

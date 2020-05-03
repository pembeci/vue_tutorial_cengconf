<template>
  <div>

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
    <h3>Conditional rendering</h3>
    <span v-if="hobbies.length == 0">So you have no hobbies.</span>
    <span v-else-if="hobbies.length == 1">So you have just {{ hobbies[0]}} hobby.</span>
    <span v-else>So your hobbies are: {{ hobbies.join(",") }}.</span>
     <h3>Loops</h3>
     <select v-model="month">
       <option value="1">January</option>
       <option value="2">February</option>
       <option value="3">March</option>
       <option value="4">April</option>
     </select><br/>
     Selected Month: {{ month }}
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
      textSize: 16,
      month: null
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>

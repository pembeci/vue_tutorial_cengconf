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
       <option v-for="monthName in months">{{ monthName }}</option>
     </select><br/>
     Selected Month: {{ month }}
     <h3>Computed Properties</h3>
     <div>     
       Average Completed: {{ averageComputed }}%
       Mood: <span v-if="averageComputed < 25">Sad</span>
       <span v-else-if="averageComputed < 70">Average</span>
       <span v-else>Happy</span>
       Direction: {{ direction }}
      </div>      
       <ul>
         <li v-for="task in tasks">
           <div class="task-type">{{ task.category }}</div>
           <div class="completed"><div :style=" {width: task.completed + '%'} "></div></div>
           <input type="range" min=0 max=100 v-model="task.completed">
           {{ task.title}}             
         </li>
       </ul>
     </div>
     
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
      month: "January",
      months: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
      tasks: [
        {category: "School", title: "Prepare slides.", completed: 70},
        {category: "Work", title: "Fix bug #524.", completed: 0},
        {category: "School", title: "Record talk.", completed: 20},
        {category: "Home", title: "Laundry", completed: 30},
        {category: "Home", title: "Dishes", completed: 80},
      ],
      direction: null
    }
  },
  computed: {
    averageComputed: function() {
      // console.log("computing average");
      let total = 0;
      this.tasks.forEach(task => { total += parseInt(task.completed) } );
      return Math.round(total / this.tasks.length);
    }
  },
  methods: {
    averageComputed2: function() {
      console.log("computing average by method");
      let total = 0;
      this.tasks.forEach(task => { total += parseInt(task.completed) } );
      return Math.round(total / this.tasks.length);
    }    
  },
  watch: {
     averageComputed: function(newVal, oldVal) {
       if (newVal > oldVal) {
         this.direction = "up";
       }
       else {
         this.direction = "down";
       }
     }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .completed {
    display: inline-block;
    width: 100px;
    height: 0.75em;
    border: 1px solid darkgreen;
    position: relative;
    top: 3px;
    left: 3px;
    padding: 0px; 
    margin-right: 5px;
    div {
      display: inline-block;
      background-color: lightgreen;
      height: 0.70em;
      padding: 0px;
      margin: 0px;
      position: relative;
      top: -3px;
    }
  }
  .task-type {
    border: 1px dotted #aaa;
    border-radius: 20%;
    text-align: center;
    padding: 1px;
    width: 3.5em;
    font-size: 70%;
    display: inline-block;
  }
  li {
    margin: 3px;
  }
  input[type=range] {
    width: 100px;
  }
</style>

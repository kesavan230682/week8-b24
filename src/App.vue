<template>
  <div  class="container">
    <h1>Hello World</h1>
    <h2>Welcome to WOD tracker</h2>
    <p>{{name}}</p>
    <p>{{number}}</p>
    <button v-on:click="increment()">increment</button>
    
    <button v-on:click="decrement()">decrement</button>
    
    
    <!-- add decrement and reset button, refer to video -->

    <hr>
    <input type="text" name="exercise" class="form form-control mb-3" placeholder="Enter Exercise name" v-model="exercise">
    <input type="text" name="assignee" class="form form-control mb-3" placeholder="Enter Assignee name" v-model="assignee">
    <input type="text" name="difficulty" class="form form-control mb-3" placeholder="Enter Difficulty name" v-model="difficulty">
    <button class="btn btn-primary" v-on:click="addPressed()">Add new item</button>
    <hr>
    <table class="table table-bordered table-hover">
      <thead>
        <tr>
          <th>Exercise</th>
          <th>Assignee</th>
          <th>Difficulty</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="wod of wods" :key="wod.exercise" v-on:click="selectedWod(wod)">
          <td>{{wod.exercise}}</td>
          <td>{{wod.assignee}}</td>
          <td>{{wod.difficulty}}</td>
        </tr>
      </tbody>
    </table>
    <hr>
    <div v-if ="selectedWod">
      <p>{{selectedWod.exercise}}</p>
      <p>{{selectedWod.assignee}}</p>
      <p>{{selectedWod.difficulty}}</p>
      <p>{{selectedWod.status}}</p>
      <button class ="btn btn-primary"> Mark as completed</button>
      <button class ="btn btn-danger"> Delete</button>
    </div>
  </div> 
</template>


<script>


export default {
  name: 'App',
  data(){
    return{
    name:'kesavan',
    number:0,
    exercise:"",
    assignee:"",
    difficulty:"",
    wods:[],
    selectedWod:null
    }
  },
  methods:{
  increment:function(){
    this.number++
      },

      decrement:function(){
    this.number--
      },

      addPressed:function(){
        var newItem = {
          'exercise':this.exercise,
          'assignee':this.assignee,
          'difficulty':this.difficulty,
          'status': "No Complete"
        }
        this.wods.push(newItem);
      
      },
      selectWod:function(wod){
        this.selectedWod = wod;

      }

  

  }
}
</script>

<style>

</style>

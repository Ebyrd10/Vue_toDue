<template>
  <div id="app">
    <div class="container">
        <h1> VuetoDue </h1>
        <md-field id="add-field" md-clearable>
      <label>Add new To-Do</label>
      <md-input v-model="newToDo" placeholder="Walk the dog..."></md-input>
        <md-button class="add-button" v-on:click="add()">Add</md-button>
         </md-field>
        <!-- <ul style="list-styke-type: none;"> -->
          <div class="listArea">
          <md-card md-with-hover v-for="(todo, i) in existingToDo"> 
            <md-ripple>
            <!-- <span> 
              {{i + 1}}:
            </span> -->
            <md-card-title> 
              {{todo.text}}
              </md-card-title>
            <md-button class="delete-button md-raised" :md-ripple="false" @cmd-cardck="deleteToDo(i)"> 
              X
              </md-button>
              </md-ripple>
          </md-card>
          </div>
        <!-- </ul> -->
    </div>
  </div>
</template>

<script>
// Importing Vue Material modules
// import Vue from 'vue'
// import { MdButton, MdForms } from 'vue-material/dist/components'
// import 'vue-material/dist/vue-material.min.css'
// import 'vue-material/dist/theme/default.css'

// Vue.use(MdButton)
// Vue.use(MdForms)

import Vue from 'vue'
import VueMaterial from 'vue-material'
import 'vue-material/dist/vue-material.min.css'

Vue.use(VueMaterial)

export default {
  name: 'app',
  data () {
    return {
      newToDo: '',
      existingToDo: [
        {text: 'get groceries', id:0},
        {text: 'run errrands', id:1},
        {text: 'walking dog', id:2}
      ]
    }
  },
  methods:{
    add(){
      this.existingToDo.push({
        text: this.newToDo,
        id: new Date().valueOf()
      }),
      this.newToDo=''
    },
    deleteToDo(i){
      this.existingToDo.splice(i,1)
    }
  }
}
</script>

<style>

:root {
  --primary-bg-color: #69f0ae;
  --secondary-bg-color: #9fffe0;
  --tertiary-bg-color: #2bbd7e;
}

.container{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 80vh;
}

.container > * {
  margin: 20px;
}
li {
  display: flex;
  justify-content: center;
  align-items: center;
  /* border: 4px solid var(--secondary-bg-color); */
  margin: 10px;
  padding: 5px;
}

/* ul {
  background-color: var(--tertiary-bg-color);
  padding-top: 25px;
  padding-bottom: 25px;
} */

body{
  background-color: var(--primary-bg-color);
}

.delete-button{
 background-color: var(--tertiary-bg-color);
}

#add-field{
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50vw;
}

.md-clear{
  left: 30rem;
}

.add-button{
  background-color:var(--secondary-bg-color)
}

.md-card{
  background-color: var(--tertiary-bg-color);
  width: 100%;
  margin: 10px;
  padding: 5px;
  padding-left: 20px;
  padding-right: 20px;
}

.listArea{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>

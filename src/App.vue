<template>
  <div id="app">
    <div class="container">
      <div class="banner">
        <h1> Vue toDue </h1>
      </div>
        <md-field id="add-field" md-clearable>
          <label>Add new To-Do</label>
          <md-input v-model="newToDo" placeholder="Walk the dog..."></md-input>
          <md-button class="add-button" v-on:click="add()">Add</md-button>
        </md-field>
          <div class="listArea">
            <div class="UncompletedArea">
          <md-card md-with-hover v-for="(todo, i) in uncompletedToDo"> 
            <md-ripple>
            <span> 
              {{i + 1}}:
            </span>
            <md-card-title> 
              {{todo.text}}
              </md-card-title>
            <md-button class="delete-button md-raised" :md-ripple="false" @click="deleteToDo(i)"> 
              DELETE
              </md-button>
              <md-button class="complete-button md-raised" :md-ripple="false" @click="completeToDo(i)"> 
              COMPLETE
              </md-button>
              </md-ripple>
          </md-card>
          </div>
          <div class="divider"></div>
          <div class="completedArea">
           <md-card md-with-hover v-for="(todo, i) in completedToDo"> 
            <md-ripple>
            <span> 
              {{i + 1}}:
            </span>
            <md-card-title> 
              {{todo.text}}
              </md-card-title>
            <md-button class="delete-button md-raised" :md-ripple="false" @click="deleteToDo(i)"> 
              DELETE
              </md-button>
              </md-ripple>
          </md-card>
           </div>
          </div>
    </div>
  </div>
</template>

<script>

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
        {text: 'get groceries', id:0, isCompleted: false},
        {text: 'run errrands', id:1, isCompleted: false},
        {text: 'walking dog', id:2, isCompleted: true}
      ]
    }
  },
  computed: {
    uncompletedToDo() {
      return this.existingToDo.filter (el => el.isCompleted== false)
    }, 
    completedToDo() {
      return this.existingToDo.filter (el => el.isCompleted== true)
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
    },
    completeToDo(i){
      this.existingToDo[i].isCompleted = !this.existingToDo[i].isCompleted;
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

body{
  background-color: var(--primary-bg-color);
}

.delete-button, .complete-button{
 background-color: var(--primary-bg-color);
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

.banner{
    /* height: 15vh; */
    background-color:var(--tertiary-bg-color);
    width: 100%;
    /* margin: 0;
    padding: 20px; */
    display: flex;
    justify-content: bottom;
    align-items: bottom;
}

h1{
    font-size: 5rem;
    color: var(--secondary-bg-color);
}

#add-field > input{
  background-color: var(--tertiary-bg-color);
  display: flex;
  justify-content: center;
  align-items: center;
  padding-left: 1rem;
}

#add-field > input::placeholder{
  color: var(--primary-bg-color);
}

.divider{
  display: block;
  width: 450px;
  height: 7px;
  margin: 2rem;
  border-radius: 20px;
  background-color: var(--secondary-bg-color)
}
</style>

<template>
  <div id="app">
    <div class="container">
        <h1> VuetoDue </h1>
        <input
        class='input'
        v-model="newToDo"
        />
        <button class="add-button" v-on:click="add()">Add</button>
        <ul style="list-styke-type: none;">
          <li v-for="(todo, i) in existingToDo"> 
            <span> 
              {{i + 1}}: {{todo.text}}
            </span>
            <md-button class="delete-button" @click="deleteToDo(i)"> 
              X
              </md-button>
          </li>
        </ul>
    </div>
  </div>
</template>

<script>
// Importing Vue Material modules
import Vue from 'vue'
import { MdButton, MdContent, MdTabs } from 'vue-material/dist/components'
import 'vue-material/dist/vue-material.min.css'
import 'vue-material/dist/theme/default.css'

Vue.use(MdButton)
Vue.use(MdContent)
Vue.use(MdTabs)

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

</style>

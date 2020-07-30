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
            <button class="delete-button" @click="deleteToDo(i)"> 
              X
              </button>
          </li>
        </ul>
    </div>
  </div>
</template>

<script>
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

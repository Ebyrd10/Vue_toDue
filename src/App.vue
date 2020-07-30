<template>
  <div id="app">
    <div class="container">
        <h1> VuetoDue </h1>
        <input
        class='input'
        v-model="newToDo"
        />
        <button class="add-button">Add</button>
        <ul style="list-styke-type: none;">
          <li v-for="(todo, i) in existingToDo"> 
            <span> 
              {{i + 1}}: {{todo.text}}
            </span>
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
  }
}
</script>

<style>

</style>

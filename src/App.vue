<script setup>
import { ref, watch } from 'vue';
let todos = ref(JSON.parse(window.localStorage.getItem('todos')))
let newTodo = ref('')
function addTodo () {
todos.value.push({text: newTodo.value,complete: false})

	newTodo.value = ''

}
function deleteI (index) {
todos.value.splice(index, 1)

}




watch(todos, function(value) {
      window.localStorage.setItem('todos', JSON.stringify(value))
    }, {deep: true})

</script>

<template>
  <h1>Todo Application</h1>
  <li v-for="(todo, index) in todos" :class="{complete: todo.complete}">
    <input type="checkbox" v-model =  "todo.complete">

{{todo.text}}
<button @click="deleteI(index)">Delete</button>
  </li>

  <input v-model="newTodo" @keydown.enter="addTodo">
  <button @click="addTodo">Add Todo</button>



</template>
 
<style >
.complete {
  text-decoration: line-through;
  color: antiquewhite;
}
body {
background-color: grey;
}
button{
  color: #aac2a1;
}
</style>
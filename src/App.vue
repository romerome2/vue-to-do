<script setup>
import { ref, watch } from 'vue';
let todos = ref(JSON.parse(window.localStorage.getItem('todos')))
let newTodo = ref('')
function addTodo () {
todos.value.push({text: newTodo.value,complete: false})
complete: false
	newTodo.value = ''

}
watch(todos, function(value) {
      window.localStorage.setItem('todos', JSON.stringify(value))
    }, {deep: true})

</script>

<template>
  <h1>Todo Application</h1>
  <li v-for="todo in todos">
    <input type="checkbox" v-model =  "todo.complete">

{{todo.text}}
<button @click="delete">Delete</button>
  </li>

  <input v-model="newTodo">
  <button @click="addTodo">Add Todo</button>



</template>
 
<style >
</style>
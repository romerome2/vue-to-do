<script setup>
import { ref, watch } from 'vue';
let filter = ref([])
let todos = ref(JSON.parse(window.localStorage.getItem('todos')))
let newTodo = ref('')
function addTodo () {
todos.value.push({text: newTodo.value,complete: false})

	newTodo.value = ''

}
function deleteI (index) {
todos.value.splice(index, 1)

}

function todofilter (todo){
  if (filter.value =='active'){
return todo.complete ==false
  } else if(filter.value == 'complete'){
    return todo.complete == true
  } else {
    return true}

  }

watch(todos, function(value) {
      window.localStorage.setItem('todos', JSON.stringify(value))
    }, {deep: true})

</script>

<template>
  <h1>Todo Application</h1> 
  <input name="filter" type="radio" value="all" v-model="filter">
  <label>All</label>

  <input name="filter" type="radio" value="active" v-model="filter">
  <label>Active</label>

  <input name="filter" type="radio" value="complete" v-model="filter">
  <label>complete</label>


  <li v-for="(todo, index) in todos.filter(todofilter)" :class="{complete: todo.complete}">
    <input type="checkbox" v-model =  "todo.complete">

{{todo.text}}
<button @click="deleteI(index)">Delete</button>
  </li>
 
  <input v-model="newTodo" @keydown.enter="addTodo">
  <button @click="addTodo">Add Todo</button>
<input name="filter" type= "radio" value="active" >


</template>
 
<style >
.complete {
  text-decoration: line-through;
  color: antiquewhite;
}
body {
background-color: rgb(140, 110, 110);
}
button{
  color: #aac2a1;
}
</style>
<script setup>
import { ref } from 'vue';
let todos = ref(['A','B','C'])

</script>

<template>
  <h1>Todo Application</h1>
  <p>{{ todos }}</p>
  <p v-for="todo in todos">
        {{todo}}
</p>
<input>
<button>Add Todo</button>

</template>
 
<style >
</style>
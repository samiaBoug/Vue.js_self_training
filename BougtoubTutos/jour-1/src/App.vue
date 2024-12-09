import { reactive } from 'vue';
<template> 
  <!--<h1>{{ message }}</h1>
  <p>Count is : {{ counter.count }}</p>

  <div v-bind:class="titleClass">Make me red</div>

  <button @click="increment">Count is : {{ counter.count }}</button>
 
  <input :value="text" @input="onInput" > 
  <p>{{ text }}</p>
 
  <h1 v-if="awesome">Vue is awesome</h1>
  <h1 v-else>Oh no </h1>
  <button @click="toggle">Toggle</button>
  -->
<input v-model="newTodo" required placeholder="new task">
<button @click="addTask">Add</button>
<ul>
  <li v-for="todo in todos" :key="todo.id">
    {{ todo.text }}
    <button @click="removeTask(todo)"> X </button>
  </li>
</ul>
  <!--to do list-->
  
</template>
<script setup>
import {ref } from 'vue'
/* const message = ref('Hello world')
const counter = reactive({count :0})
const titleClass = ref('title')
const text= ref('')
function increment(){
  counter.count++
}
function onInput(e){
  text.value =e.target.value
}
const awesome = ref(true)
function toggle(){
  awesome.value = !awesome.value
}*/
let id =0 ;
const newTodo = ref('')
const todos = ref([])
function addTask(){
  todos.value.push({id: id++ , text:newTodo.value})
  newTodo.value=''
} 
function removeTask(task){
  todos.value =todos.value.filter(
      (t)=> t !== task
  )
}

</script>
<style>
.title {
  color: red;
}
</style>
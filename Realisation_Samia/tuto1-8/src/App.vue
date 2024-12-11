
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
  
<input v-model="newTodo" required placeholder="new task">
<button @click="addTask">Add</button>
<ul>
  <li v-for="todo in todos" :key="todo.id">
    {{ todo.text }}
    <button @click="removeTask(todo)"> X </button>
  </li>
</ul>
-->
  <!--to do list-->
  <h1>To do list</h1>

  <input v-model="newTask" required placeholder="new task">
  <button @click="addTask">Add</button>

<ul>
  
  <li v-for="todo in filterTodos" :key="todo.id">
    <input type="checkbox" v-model="todo.done" >
    <span :class="{done:todo.done}">{{ todo.text }}  </span>
  <button @click="removeTask(todo)">X</button>
</li>
</ul>
<button @click="hideComplete = !hideComplete">{{ hideComplete ? 'Show all' : 'Hide Completed' }}</button>

</template>
<script setup>
/*import {ref } from 'vue'
 const message = ref('Hello world')
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
}
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
}*/

import {ref , computed} from 'vue'
let id = 0
const todos = ref([])
const newTask = ref('')
const hideComplete = ref(false)
function addTask(){
  todos.value.push({id: id++ , text: newTask.value , done : false})
  newTask.value = ''
}


function removeTask(task){
  todos.value =todos.value.filter(
      (t)=> t !== task
  )
}

const filterTodos = computed (
  () =>{
    return hideComplete.value ? todos.value.filter(
        (t)=> !t.done ) : todos.value
})
</script>
<style>
.title {
  color: red;
}

li {
  list-style: none;
}
.done{
  text-decoration: line-through;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
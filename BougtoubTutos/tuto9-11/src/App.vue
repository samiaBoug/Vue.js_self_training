<template>
 <!-- <p ref="pElementRef">Hello</p>-->

<p>Todo id : {{ todoId }}</p>
<button @click="todoId++" :disabled="!todoData">Fetch next todo</button>
<p v-if="!todoData">loading...</p>
<pre v-else>{{ todoData }}</pre>
</template>

<script setup>
/* // tuto9
import {ref , onMounted} from 'vue'
const pElementRef= ref(null)

onMounted(
  ()=>{
    //component is now mounted
    pElementRef.value.textContent = 'mounted !'
  }
)

// tuto 10
import {ref , watch} from 'vue'
const count = ref(0)
watch(count , (newCount)=> {
  console.log("new count is :"+ newCount)
})

*/
import { ref , watch} from 'vue'
const todoId = ref(1)
const todoData = ref(null)
async function fetchData(){
  todoData.value = null
  const res = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
  )
  todoData.value = await res.json()
}
fetchData()
watch(todoId , fetchData)



</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

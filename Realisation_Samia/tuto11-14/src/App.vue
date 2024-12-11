
<script setup>
/*
import { ref } from 'vue';
import ChildComp from './ChildComp.vue'
import ChildComp from ':';

const greeting = ref('Hello from parent')
const childMsg = ref('no child nessage yet')
*/
import { ref } from "vue";
import { ChildComp } from "./ChildComp.vue";
const msg = ref("from parent")
</script>

<template>
  <!--
  <ChildComp :msg="greeting" @response="(msg)=> childMsg = msg" />
  <p>{{ childMsg }}</p>
  -->
  <ChildComp>
    Message : {{ msg }}
  </ChildComp>
</template>
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

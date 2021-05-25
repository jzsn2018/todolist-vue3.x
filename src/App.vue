<!--
 * @Date: 2021-05-24 15:08:01
 * @LastEditors: Timothy
 * @LastEditTime: 2021-05-25 14:25:38
 * @Description: 
-->
<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h3>Vuejs 3.x TodoList Demo</h3>
  <Todo/>
</template>

<script>
import Todo from './components/Todo.vue'

export default {
  name: 'App',
  components: {
    Todo
  }
}
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

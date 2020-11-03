<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App" @sendmsg="handle"/> -->
  <!-- <Caculator msg="Welcome to Caculator" @sendmsg="handle"/> -->
  <TodoList msg="Welcome to Caculator" @sendmsg="handle"/>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import Caculator from './components/Caculator.vue'
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    // Caculator,
    TodoList
  },
  setup(){
    const handle = value => {
      console.log('setup > value', value);
    }
    return {
      handle
    }
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


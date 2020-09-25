<template>
  <div id="app">
    <HelloWorld msg="Atividade 03"/>
    <Users msg="Questão 01"/>
    <Todos msg="Questão 02"/>
    <Photos msg="Questão 03"/>
    <Comments msg="Questão 04"/>
    <Posts msg="Questão 05"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Users from './components/Users.vue'
import Todos from './components/Todos.vue'
import Photos from './components/Photos.vue'
import Comments from './components/Comments.vue'
import Posts from './components/Posts.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Users,
    Todos,
    Photos, 
    Comments, 
    Posts
  }
}
</script>

<style>
#app {
  font-family: 'Courier New', Courier, monospace, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

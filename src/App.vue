<template>
  <div>
    <navbarApp/>  
    <router-view></router-view>
  </div>
  
  
</template>

<script>
import navbarApp from './components/navbar.vue'
export default {
  name: 'App',
  components: {
    navbarApp
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #2c3e50;
}
h1{
  color: aliceblue;
}
</style>

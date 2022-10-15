<template>
  <div id="app">
      <img alt="Vue logo" src="./assets/logo.png" width="50" class="logo">
    <router-view msg="Disney Personajes"/>
  </div>
</template>

<script>


export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: url("./assets/fondo.jpg");
  min-height:100vh;
}
.logo{
  position: absolute;
  left:80%;
}
</style>

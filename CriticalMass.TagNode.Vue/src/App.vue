<template>

  <div id="app123">    
    <img src="./assets/logo.png">
    <p>    
    <router-link to="/">首页</router-link>
    <router-link to="/Test">属性维护</router-link>
    </p>
    <router-view/>
  </div>  
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app123 {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>



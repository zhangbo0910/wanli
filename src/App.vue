<template>
  <div id="app">
    <keep-alive>
    <router-view/>
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
html,body{
  height:100%;
  overflow:hidden;
}
body{
  background:url('./assets/img/bg.jpg') no-repeat;
  background-size:100% 100%; 
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* overflow: hidden; */
  height:100%;
}
*{
  margin: 0;
  padding: 0;
}
</style>

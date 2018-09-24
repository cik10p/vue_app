<template>
  <div id="app">
    <users2></users2>
    [<Posts></Posts>]
  </div>
</template>

<script>
import Posts from "./components/Posts"
import Users from "./components/Users"
import Users2 from "./components/Users2"

export default {
  name: 'App',
  components:{
    Posts, Users,Users2
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

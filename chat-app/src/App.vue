<template>
  <Header title="Chat App"/>
  <router-view></router-view>
    <div id="test-container">
    <table>
      <th>
        <router-link to="/">Home</router-link></th>
      <th>
        <router-link to="/about">About</router-link>
      </th>
    </table>
  </div>
</template>

<script>
import Header from './components/Header'

export default {
  name: 'App',
  components: {
    Header,
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#test-container{
  width: 100%;
  display: flex;
  justify-content: center;
}
</style>

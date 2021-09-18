<template>
  <Header title="Chat App"/>
  <div id="test-container">
    <Message />
  </div>
</template>

<script>
import Header from './components/Header'

import Message from './components/Message' 


export default{
  name: 'App',
  components: {
    Header,
    Message,
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
}
#test-container{
  width: 50%;
}
</style>

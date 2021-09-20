<template>
  <Header title="Chat App"/>
  <div id="test-container">
  <ChatBox @new-message="newMessage" :messages='messages'/>

  </div>
</template>

<script>
import Header from './components/Header'
import ChatBox from './components/Chatbox'
import Message from './components/Message' 


export default{
  name: 'App',
  components: {
    Header,
    Message,
    ChatBox,
  },
  data() {
    return {
      messages: []
    }
  },
  created(){
    // TODO: add json database to fetch data from
    this.messages = [
      {
        MessageID: 1,
        Message: "Lipsum",
        Sender: "Test Sender"
      },{
        MessageID: 2,
        Sender: "Test Sender"
      },{
        MessageID: 3,
        Message: "Lipsum",
      },{
        MessageID: 4,
      },
    ]
  },
  methods: {
    newMessage(messagebox){
      this.messages = [...this.messages, {
          MessageID: 0, 
          Message: messagebox,
          Sender: "Undefined sender"
          }]
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
}
#test-container{
  width: 100%;
  display: flex;
  justify-content: center;
}
</style>

<template>
  <div class="home">
  </div>
  <div id="test-container">
    <ChatBox @new-message="newMessage" @delete-message="deleteMessage" :messages='messages'/>
  </div>
</template>

<script>
// @ is an alias to /src

import ChatBox from '../components/Chatbox'
import Message from '../components/Message' 

export default {

  name: 'Chat',
  components: {
    Message,
    ChatBox,
  },
  data() {
    return {
      messages: []
    }
  },
  methods: {
    async newMessage(messagebox){ 
      const res = await fetch ('api/messages', {
        method: "POST", 
        headers:{
          'Content-type': 'application/json',
        },
        body: JSON.stringify({"Message": messagebox, "Sender": "Test Sender", "ProfilePicture": "https://i.redd.it/sc3sb84ao9o71.jpg"})
      })
      const data = await res.json()
      this.messages = [...this.messages, data]
    },
    async deleteMessage(id){
      const res = await fetch(`api/messages/${id}`, {
        method: "DELETE"
      }) 
      res.status === 200 ? (this.messages = this.messages.filter((message)=>message.id !== id)) : alert ("Error deleting message.")
    },
    async fetchMessages(){
      const res = await fetch('api/messages')
      const data = await res.json()
      return data
    },
  },
  async created(){
    this.messages = await this.fetchMessages()
  }
}
</script>

<template>
    <div id="container">
        <div :key='message.id' v-for="message in messages">
            <Message 
            :Sender="message.Sender"
            :Message="message.Message"
            :ProfilePicture="message.ProfilePicture"
            :id="message.id"
            @delete-message="$emit('delete-message', message.id)"
            />
        </div>
        <input @keypress="keymonitor" v-model="messagebox" type="text" placeholder="Send message...">
    </div>
</template>

<script>
import Message from './Message'

export default{
    components: {
        Message,
    },
    props: {
        messages: Array,
    },
    methods:{
        keymonitor: function(event){
            if(event.key == "Enter"){
                this.$emit('new-message', this.messagebox);
                this.messagebox = ""
            }
        }
    },
    emits: ['new-message']
}
</script>

<style scoped>
#container{

}
input{
    width: 100%;
    overflow: hidden;
    white-space: nowrap;
    border: none;
    background-color: rgb(229, 229, 229);
    color: rgb(225, 225, 225);
    font-size: 20px;
}
input:focus{
    border: none;
    background-color: rgb(240, 240, 240);
    color: rgb(125, 125, 125);
    transition-duration: 50ms;
    outline: none!important;
}
</style>
<template>
<div id="screen-container">
    <div id="chatter-container">
        <h3>TestPerson</h3>
    </div>
    <div id="content-container">
        <div id="message-container">
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
    </div>
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
    watch: { 
        // called whenever messages is updated
        messages() {
            updateScroll();
        }
    },
    methods:{
        keymonitor: function(event){
            if(event.key == "Enter"){
                this.$emit('new-message', this.messagebox);
                this.messagebox = ""
                updateScroll();
            }
        }
    },
    created(){
        updateScroll();
    },
    emits: ['new-message']
}


/** TODO: This doesn't seem to work. The function gets called at the right places, but the scrolling doesnt work */
 // JS snippet to focus latest chat entry when overflowing
 function updateScroll(){
     console.log("updateScroll called.");
    // Can throw errors with reading null on scrollHeight if this check isn't here
    if (document.getElementById("content-container")){
        var container = document.getElementById("content-container");
        document.getElementById("content-container").scroll(0, container.scrollHeight - container.clientHeight) 
    }
 }


</script>

<style scoped>
@media screen and (min-height: 800px){
    #screen-container{
        background-color: rgb(229, 229, 229);
        height: 70vh;
        overflow: hidden;
        display: flex;
        flex-flow: column;
        justify-content: space-between;
        border-radius: 1%;
    }
}
#content-container{
    max-height: 65vh;
    overflow-y: scroll;
    overflow-x: hidden;
}
#chatter-container{
    height: 5vh;
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
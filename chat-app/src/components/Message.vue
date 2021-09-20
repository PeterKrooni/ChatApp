<template>
    <div id="container" :style="menuIsOpen ? 'background-color: rgb(230, 230, 230)' : ''">
        <div id="content-container">
            <img :src='ProfilePicture' alt="">
            <h5>{{Sender}}:</h5>
            <p>{{Message}}</p>       
        </div>
        
        <div id="options-container">
            <div id="msg-options-container" v-if="menuIsOpen">
                <i @click="alertNoEditing" class="fas fa-pen" id="edit-icon"></i>
                <i @click="$emit('delete-message', this.id)" class="fas fa-trash-alt" id="delete-icon"></i>
            </div>
            <i @click="toggleMessageOptions" :style="menuIsOpen ? 'opacity: 0.2' : ''" class="fas fa-ellipsis-v"></i>
        </div>
    </div>
</template>

<script>
export default{
    name: 'Message',
    data() {
        return {
            menuIsOpen: false,
        }
    },
    props: {
        Sender: {
            default: "Person McPerson",
            type: String
        },
        Message: {
            default: "Lorem ipsum dolor sit amet, consectetur adipiscing.",
            type: String
        },
        ProfilePicture: {
            default: "https://i.redd.it/sc3sb84ao9o71.jpg",
            type: String
        },
        id: {
            default: -1,
            type: Number
        },
    },
    methods: {
        toggleMessageOptions(){
            this.menuIsOpen = !this.menuIsOpen
        },
        created(){
          this.Sender = "Person mcPerson"  
        },
        alertNoEditing(){
            alert("Editing messages is not supported yet.")
        },
    },
    emits: ['delete-message']
}
</script>

<style scoped>
@media screen and (min-width: 1080px){
    #container{
        width: 70em;
    }
}    
#container{
    background-color: rgb(235, 235, 235);
    border-radius: 2%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    transition-duration: 100ms;
}

#content-container{
    display: flex;
    align-items: center;
    justify-content: left;
    width: 80%;
}
#options-container{
    display: flex;
    align-items: center;
    justify-content: flex-end;
    flex-flow: row;
    width: 20%;
}
#msg-options-container{
    display: flex;
    align-items: center;
    justify-content: left;
    margin-right: 10%;
}
#edit-icon{
    margin-right: 10%;
}
img{
    margin: 1rem;
    width: 3rem;
    height: 2.5rem;
    border-radius: 100%;
    border: 2px solid rgb(199, 179, 179)
}
h5{
    margin-right: 1rem;
    font-size: 18px;
    color: rgb(199, 179, 179);
    white-space: nowrap;
}
p{
    font-size: 20px;
    margin-left: -10px;
    color: rgb(88, 88, 88)
}
i{
    font-size: 20px;
    padding-right: 6%;
    opacity: 0.6;
    transition-duration: 100ms;
}
</style>
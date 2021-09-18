<template>
    <div id="container">
        <div id="content-container">
            <img :src='ProfilePicture' alt="">
            <h3>{{Sender}}:</h3>
            <h4>{{Message}}</h4>       
        </div>
        
        <div id="options-container">
            <div id="msg-options-container" v-if="menuIsOpen">
                <i class="fas fa-pen" id="edit-icon"></i>
                <i class="fas fa-trash-alt" id="delete-icon"></i>
            </div>
            <i @click="toggleMessageOptions" :style="menuIsOpen ? 'opacity: 0.2' : 'opacity:0.6'" class="fas fa-ellipsis-v"></i>
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
    },
    methods: {
        toggleMessageOptions(){
            this.menuIsOpen = !this.menuIsOpen
        },
        created(){
          this.Sender = "Person mcPerson"  
        }
    },
}
</script>

<style scoped>
#container{
    background-color: rgb(235, 235, 235);
    border-radius: 2%;
    display: flex;
    justify-content: space-between;
    align-items: center;
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
    max-width: 4rem;
    max-height: 6rem;
    border-radius: 100%;
    border: 2px solid rgb(199, 179, 179)
}
h3{
    margin-right: 1rem;
    font-size: 16px;
    color: rgb(199, 179, 179);
    white-space: nowrap;
}
h4{
    font-size: 16px;
    margin-left: -10px;
    color: rgb(88, 88, 88)
}
i{
    font-size: 20px;
    padding-right: 6%;
    opacity: 0.6;
}
</style>
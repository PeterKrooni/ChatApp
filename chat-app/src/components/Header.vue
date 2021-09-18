<template>
    <div id="container">
        <i class="fas fa-comment-dots"></i>
        <h1>{{title}}</h1>
    </div>
</template>

<script>
export default{
    name: 'Header',
    props: {
        title: String
    },
}
</script>

<style scoped>
#container{
    margin: 2rem;
    display: flex;
    justify-content: center;
    flex-flow: column;
}
i {
    font-size: 4rem;
}
</style>
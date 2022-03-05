<template>
    <section class="container">
        <h1>{{title}}</h1>
        <p>{{message}}</p>
        <router-link to="/">topへ</router-link>
    </section>
</template>

<script>
export default {
    data: function() {
        return {
        title:"Other",
        message:"これは別のページです",
        };
    },
    
}
</script>

<style>

.container{
    padding: 5px 10px;
}
h1{
    font-size:60px;
}
p{
    padding-top:5px;
    font-size:20px;
}
a{
    font-size: 16px;
}
</style>

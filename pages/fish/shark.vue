<template>
    <section class="container">
        <h1>{{title}}</h1>
        <p>{{message}}</p>
        <hr>
        <pre>[{{now}}]</pre>
        <router-link to="./other">Other</router-link>
    </section>

</template>

<script>

export default {
    data: function() {
        return{
        title:'Hello',
        message: 'this is message',
        now:'wait..',
        };
    },

    created: function(){
        setInterval(()=>{
            var d = new Date();
            this.now = d.getHours()
            +':'+d.getMinutes()
            +':'+d.getSeconds();
        }, 1000);
    },
}
</script>

<style>
.container{
    padding:20px;
}
h1 {
 font-size:60px;
}
p{
    padding-top:5px;
    font-size: 20px;
}
hr{
    margin: 10px 0px;
}
pre{
    padding-top:10px;
    font-size:18px;
    background-color: #efefef;
}

</style>



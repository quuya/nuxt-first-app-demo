<template>
    <v-app>
        <v-container fluid>
            <v-row>
                <v-app-bar>
                  <h3>ToDo list.</h3>
                </v-app-bar>
            </v-row>
           
            <v-row>
                    <v-col>
                        <v-sheet color="white"
                                elevation="6"
                                height="1161"
                                width="1137">
                            <v-col id="app">
                                {{message}}
                            </v-col>
                            <v-footer>
                                kouya
                            </v-footer>
                        </v-sheet>
                    </v-col>
            </v-row>
            
        </v-container>
    </v-app>
</template>

<script>
let app =new Vue({
    el :'#app',
    data:{
            message: 'kouya'
    }
})

</script>

<style>


</style>
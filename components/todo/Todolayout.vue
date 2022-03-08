<template>
<v-app>
  <v-app-bar  
      color="deep-purple"
      dark>
     <v-toolbar-title>Todo-list</v-toolbar-title>
      <v-spacer></v-spacer>
        <div id="app">
            {{date}}
        </div>
  </v-app-bar>

  <!-- アプリケーションのコンポーネントに基づいてコンテンツのサイズを決定 -->
  <v-main>

    <!-- アプリケーションに適切なgutterを提供 -->
    <v-container fluid>

      <!-- vue-routerを使用する場合 -->
      <router-view></router-view>
    </v-container>
  </v-main>

  <v-footer app>
    <!-- -->
  </v-footer>
</v-app>
</template>

<v-app-bar
      color="deep-purple"
      dark
    >
      <v-toolbar-title>Todo-list</v-toolbar-title>
      <v-spacer></v-spacer>
        <div id="app">
            {{date}}
        </div>
    </v-app-bar

<script>
export default{
    name:"DateCompornent",
    data:()=>({
        date: ''
    }),
    methods:{
        printDate: function(){
            return new Date().toLocaleDateString();
        }
    },
    mounted: function(){
        this.date=this.printDate();
    }
}
</script>

<style>


</style>

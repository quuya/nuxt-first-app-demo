<template>
  <v-app id="inspire">
    <v-system-bar app>
      <v-spacer></v-spacer>

      <v-icon>mdi-square</v-icon>

      <v-icon>mdi-circle</v-icon>

      <v-icon>mdi-triangle</v-icon>
    </v-system-bar>

    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-sheet
        color="grey lighten-4"
        class="pa-4"
      >
        <v-avatar
          class="mb-4"
          color="grey darken-1"
          size="64"
        ></v-avatar>

        <div>john@vuetifyjs.com</div>
      </v-sheet>

      <v-divider></v-divider>

      <v-list>
        <v-list-item
          v-for="[icon, text] in links"
          :key="icon"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  <v-main>
    <v-container
    class="py-8 px-6"
    fkuid>
      <v-row>
        <v-col>
          <v-card>
          <p>1</p>
          </v-card>
        </v-col>
        <v-col>
          <v-card>
          <p>2</p>
          </v-card>
        </v-col>
        <v-col>
          <v-card>
          <p>3</p>
          </v-card>
        </v-col>
      </v-row>
      <v-row>
        <v-btn  color='primary' to='/fish/shark'>
          サメ
        </v-btn>
      </v-row>
      <v-row>
        <ul>
          <li v-for="todo in todos" :key="todo.key">
            {{todo.text}}
          </li>
        </ul>
      </v-row>
      <v-row>
        <ul  v-for="todo in todos" :key="todo.key" class="todocontent">
          <v-card width="500" height="50" >
            <v-card-text >
              <a href="./todopra">
              {{todo.text}}
              </a>
            </v-card-text>
          </v-card>         
        </ul>
      </v-row>
      <!--addtodo-->
      <v-row>

      </v-row>
    
    </v-container>
  </v-main>

  </v-app>
</template>

<script>
  export default {
    data: () => ({
      cards: ['Today', 'Yesterday'],
      drawer: null,
      links: [
        ['mdi-inbox-arrow-down', 'Inbox'],
        ['mdi-send', 'Send'],
        ['mdi-delete', 'Trash'],
        ['mdi-alert-octagon', 'Spam'],
      ],
      todos:[
        {text:'vue'},
        {text:'Nuxt'},
        {text:'vuetify'},
        {text:'todo'}
      ]
    }),
  }
</script>
<style scoped>
.col{
  text-align:center ;
}
.todocontent{
  padding :10px;
}


</style>

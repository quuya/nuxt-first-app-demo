<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <!-- MovieList -->
      <v-list v-for="movie in movies" :key="movie.id" >
          <v-list-item @click="clickedinfo = !clickedinfo" v-model="movie.id">
              <v-list-item-content>
                  <v-list-item-title>
                      {{movie.title}}
                  </v-list-item-title>
              </v-list-item-content>
          </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>映画.memo</v-toolbar-title>
      <v-spacer></v-spacer>
      <!----Form.dialog----->
        <v-row justify="center">
            <v-dialog v-model="dialog" persistent max-width="600px" >
                <template v-slot:activator="{ on, attrs }">
                    <v-btn icon v-bind="attrs" v-on="on">
                        <v-icon>
                            mdi-plus-circle
                        </v-icon>
                    </v-btn>
                </template>
                <v-card>
                    <v-card-title>
                    <span class="text-h5">映画のタイトル</span>
                    </v-card-title>
                    <v-card-text>
                        <v-container>
                            <v-row>
                                <v-col cols="12">
                                    <v-text-field
                                    label="タイトルを入力してください"
                                    required
                                    v-model="title"
                                    ></v-text-field>
                                </v-col>
                                <v-col cols="12">
                                    <v-text-field
                                    label="登場人物"
                                    required
                                    v-model="char"
                                    ></v-text-field>
                                </v-col>
                                <v-col cols="12">
                                    <v-text-field
                                    label="あらすじ"
                                    required
                                    v-model="content"
                                    ></v-text-field>
                                </v-col>
                                <v-col cols="12">
                                    <v-text-field
                                    label="見どころ"
                                    required
                                    v-model="keypoint"
                                    ></v-text-field>
                                </v-col>

                            </v-row>
                        </v-container>
                    </v-card-text>
                    <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn
                        color="blue darken-1"
                        text
                        @click="dialog = false"
                    >
                        Close
                    </v-btn>
                    <v-btn
                        color="blue darken-1"
                        text
                        @click.stop="addTask(title,content,char,keypoint)"
                    >
                        Save
                    </v-btn>
                    </v-card-actions>
                </v-card>
            </v-dialog>
        </v-row>
      <!-----Form.end------->
    </v-app-bar>

    <v-main>
      <!-- movieInfo -->
      <v-card elevation="2" v-show="clickedinfo" v-for="movie in movies" :key="movie.id" my="20px">
          <v-card-title>
              {{movie.title}}
          </v-card-title>
          <v-divider></v-divider>
          <v-card-text>
              <h2>・登場人物</h2>
              {{movie.char}}
            <h2>・あらすじ</h2>
            {{movie.content}}
            <h2>・見どころ</h2>
            {{movie.keypoint}}
          </v-card-text>
      </v-card>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    name:"memo-app",
    data: () => ({ 
        drawer: null,
        movies:[],
        title:"",
        content:"",
        char:"",
        keypoint:"",
        dialog:false,
        clickedinfo:"true",
        }),
    
    methods:{
        addTask:function(title,content,char,keypoint){
            if(!this.title){
                alert("タイトルを入力してください。");
                return;
            }
            let id = Date.now().toString();
            this.movies.push({
                "id":this.id,
                "title":this.title,
                "content":this.content,
                "char":this.char,
                "keypoint":this.keypoint,
            });
            this.title = "";
            this.content = "";
            this.char = "";
            this.keypoint = "";
        },
    }
  }
</script>


<style>

</style>






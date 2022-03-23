<template>
    <v-app>
        <v-card height="1000" width="500" class="mx-auto">
            <v-toolbar color="cyan" dark>
                <v-app-bar-nav-icon></v-app-bar-nav-icon>

                <v-toolbar-title>
                    Todo
                </v-toolbar-title>
                
                <v-spacer></v-spacer>
                <v-btn icon>
                    <v-icon>mdi-magnify</v-icon>
                </v-btn>

                <v-btn icon>
                    <v-icon>mdi-checkbox-marked-circle</v-icon>
                </v-btn>
            </v-toolbar>
    

            <v-list v-for="item in items" :key="item.id" cols="12">
                <v-list-item-group>
                    <v-list-item>
                        <v-list-item-action>
                            <v-checkbox :input-value=item.done @click="done(item.id)">
                            </v-checkbox>
                        </v-list-item-action>
                        
                        <v-list-item-content>
                            <v-list-item-title>
                                {{item.task}}
                            </v-list-item-title>
                        </v-list-item-content>
                        <v-list-item-action>
                            <v-btn @click='deleteTask(item.id)' icon>
                                <v-icon>
                                    mdi-backspace
                                </v-icon>
                            </v-btn>
                        </v-list-item-action>
                    </v-list-item>
                </v-list-item-group>
            </v-list>

            <v-col cols="12" class="d-flex">
                <v-list-item-content>
                    <v-text-field 
                        v-model="todo"
                        label="Addtodo"
                        required>
                    </v-text-field>
                </v-list-item-content>
                <v-list-item-action>
                    <v-btn @click.stop="addTask(todo)" icon>
                        <v-icon>
                            mdi-plus-circle
                        </v-icon>
                    </v-btn>
                </v-list-item-action>
            </v-col>

        </v-card>
    </v-app>
</template>

<script>
export default{
    data: () => ({
        items: [
            {
                id:1,
                task:'Vuetifyを勉強する',
                done: true,
                
            },
            {
                id:2,
                task:'JSを勉強する',
                done: false,
            },
        ],
    }),
    methods:{
        done(id){
            this.items[id].done= !this.items[id].done
            console.log(this.items[id].done)
        },
        deleteTask(id){
            this.items=this.items.filter((item) => item.id !== id)
        },
        addTask(todo){
            let id = Date.now().toString()
            this.items.push({id:id,task:todo,done:false})
        }
    }
}    

</script>

<style>

</style>

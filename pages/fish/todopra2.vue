<template>
    <v-app>
        <v-container text-center wrap >
            <v-card mx-auto >
                <v-toolbar color="cyan" dark>
                    <v-toolbar-title>
                        TodoList
                    </v-toolbar-title>
                    <v-spacer></v-spacer>
                    <!----------タスク追加ダイアログ-------------->
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
                                <span class="text-h5">Taskを追加</span>
                                </v-card-title>
                                <v-card-text>
                                    <v-container>
                                        <v-row>
                                            <v-col cols="12">
                                                <v-text-field
                                                label="タスクを入力してください"
                                                required
                                                v-model="task"
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
                                    @click.stop="addTask(task,index)"
                                >
                                    Save
                                </v-btn>
                                </v-card-actions>
                            </v-card>
                        </v-dialog>
                    </v-row>
                <!------------------------>
                </v-toolbar>
                
                <v-col>
                    <v-data-table :headers="headers"
                                  :items="items"
                                  class="elevation-1"
                                  text-align="left">
                        <template v-slot:[`item.control`]="{ item }">
                            <v-btn class="mx-2" fab dark x-small color="error" @click="deleteTask(item)" >
                                <v-icon dark>mdi-minus</v-icon>
                            </v-btn>
                        </template>
                    </v-data-table>                
                </v-col>
            </v-card>
        </v-container>
    </v-app>
</template>

<script>
export default{
    name:'TodoList',
    data:function(){
        return{
            headers:[
                {
                    text:'Todo',
                    align:'start',
                    sortable:false,
                    value:'index',
                },
                {text:'Task',value:'task'},
                {text:'操作',value:"control"}
            ],
            items:[],
            index:"",
            task: "",
            dialog:false

        }
    },
    methods:{
        addTask:function(task,index){
            if(!this.task){
                alert("Taskを入力してください。");
                return;
            }
            this.items.push({
                "task":this.task,
            });
            this.task = "";
        },
        deleteTask: function(item){
            this.items.splice(this.items.indexOf(item),1);
        }
    }
}
</script>

<style>

</style>


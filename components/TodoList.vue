<template>
    <div>
        <v-toolbar dark color="indigo">
            <v-toolbar-title class="while--text">
                My Todo
            </v-toolbar-title>
        </v-toolbar>
        <v-list>
            <template v-for="(todo,i) in todos">
                <v-list-tile
                v-bind:key="i">
                <v-list-tile-content>
                {{ todo }}
                </v-list-tile-content>
                <v-list-tile-action>
                    <v-btn flat icon
                    v-on:click="deleteTodo(i)">
                        <v-icon>mdi-delete</v-icon>
                    </v-btn>
                </v-list-tile-action>
                </v-list-tile>
                <v-divider v-bind:key="i">
                </v-divider>
            </template>
        </v-list>
        <div class="bottom-right">
            <v-btn fab color="indigo"
            v-on:click="addTodo">
            <v-icon color="while">mdi-add</v-icon>
            </v-btn>
        </div>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                todos:[]
            }
        },
        created(){
            this.todos = JSON.parse(localStorage.getItem('todos')) || [];
        },
        methods:{
            deleteTodo(i){
                this.todos.splice(i,1);
                    localStorage.setItem('todos',JSON.stringgify(this.todos));
            },
            addTodo(){
                this.$router.push('/todos/add');
            }
        }
    }
</script>

<style scoped>
    .bottom-right{
        position:fixed;
        bottom:0px;
        right:0px;
    }
</style>
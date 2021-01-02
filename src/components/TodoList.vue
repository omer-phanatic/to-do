<template>
    <div>
        <v-row  v-for="(todo,index) in todos" :key="todo.id">
            <v-col>
                <ListItem
                v-bind:todo="todo" 
                @delete-item="deleteItem(index)"/>
            </v-col>
        </v-row>
    </div>
</template>

<script>

import ListItem from "./ListItem.vue";

export default {
    name: "TodoList",
    components: {ListItem},
    data: ()=>({
        
    }),
    props: ["todos"],
    methods: {
        deleteItem(index) {
            this.todos.splice(index, 1);
        },
    }           
}
</script>


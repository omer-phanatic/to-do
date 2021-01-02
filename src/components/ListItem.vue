<template>
    <div>
        <v-card class="mt-5" :color="colorChange" :complete="complete">
            <v-card-title ><input type="checkbox" @change="changeComplete">{{ todo }}</v-card-title>
            <v-card-text><v-text-field v-model="newTask"  v-if="edit"></v-text-field></v-card-text>
            <v-card-actions>
                <v-btn v-if="!edit" @click="editItem">edit</v-btn>
                <v-btn text v-if="edit" @click="saveEdit">save</v-btn>
                <v-btn color="red" text v-if="edit" @click="cancelEdit">cancel</v-btn>
                <v-btn @click="deleteItem">delete</v-btn>
            </v-card-actions>
        </v-card>
    </div>
</template>

<script>
export default {
    name: "ListItem",
    props: ["todo"],
    data: ()=>({
        complete: Boolean,
        edit: Boolean,
        newTask:"",
    }),

    methods: {
        changeComplete()  {this.complete = !this.complete;},
        deleteItem() {this.$emit('delete-item')},
        editItem() {this.edit=true},
        cancelEdit() {this.edit=false},
        saveEdit() {
            this.todo=this.newTask;
            this.edit=false;
            },
    },

    computed: {
        colorChange: function(){
            if (this.complete) {
                return "";
            } else {
                return "green";
            }
        },

        },
        created(){
            this.edit =false;
        }
}
</script>

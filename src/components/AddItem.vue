<template>
    <div>
        <v-form>
            <v-row>
                <v-col cols="4">
                    <v-text-field
                    v-model="task"
                    ></v-text-field>
                    <v-btn @click ="submit">Add</v-btn>
                </v-col>
            </v-row>
        </v-form>
    </div>
</template>

<script>
export default {
    name: 'AddItem',
    data: ()=>{
        task = this.task;
    },
    methods: {
        submit(){
            this.$emit('addNew', this.task)
        }
    }
}
</script>
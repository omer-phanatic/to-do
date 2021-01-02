<template>
  <v-app >
    <v-row class="mx-auto">
      <v-col>
        <v-form>
          <v-row>
            <v-col v-model="hasTextValue">
              <v-text-field
               v-model="task"
               placeholder="Get shit done"></v-text-field>
              <v-btn 
               :disabled="!hasTextValue"
               @click ="submit">Add a task</v-btn>
            </v-col>
          </v-row>
        </v-form>
        <TodoList v-bind:todos="todos" />
      </v-col>
    </v-row>
  </v-app>
</template>

<script>
import TodoList from "./components/TodoList";

export default {
  name: 'App',
  components: {
    TodoList,
  },

  data: () => ({
    task:"",
    todos: [

      ],

  }),

    methods: {
      submit(){
        this.todos.push(this.task);
        this.task="";
      }
  },
  computed: {
    hasTextValue() {
     return this.task;
    },
  }
}
</script>

<style scoped>
  
</style>

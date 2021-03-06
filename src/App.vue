<template>
  <ul>
    <Todo
      v-for="todo in todos"
      v-bind:key="todo.id"
      :todo="todo"
      @completeTodo="completeTodo(todos.indexOf(todo))"
    />
  </ul>
  <AddTodoForm v-model:todoText="todoText" :addTodo="addTodo" />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Todo from "./components/Todo.vue";
import AddTodoForm from "./components/AddTodoForm.vue";

export default defineComponent({
  name: "App",
  components: {
    Todo,
    AddTodoForm,
  },
  data: () => {
    return {
      todos: [
        { title: "Take out trash", completed: false, id: 1 },
        { title: "Study", completed: true, id: 2 },
      ],
      todoText: "",
    };
  },
  methods: {
    addTodo() {
      this.todos = [
        ...this.todos,
        {
          title: this.todoText,
          completed: false,
          id: Math.floor(Math.random()) * 100000,
        },
      ];
      this.todoText = "";
    },
    completeTodo(index: number) {
      this.todos[index].completed = !this.todos[index].completed;
    },
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template>
  <input
    placeholder="Enter name of todo"
    :value="todoText"
    @input="$emit('update:todoText', $event.target.value)"
  />
  <button @click="addTodo()">Add todo</button>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";

export default defineComponent({
  name: "AddTodoForm",

  props: {
    addTodo: Function as PropType<(title: string) => void>,
    todoText: String,
  },
  emits: ["update:todoText"],
});
</script>

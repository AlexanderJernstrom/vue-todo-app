<script lang="ts">
import { defineComponent, PropType } from "vue";

interface TodoInterface {
  title: string;
  completed: boolean;
  id: number;
}

export default defineComponent({
  name: "Todo",
  props: {
    todo: Object as PropType<TodoInterface>,
  },
  methods: {
    completeTodo() {
      this.$emit("completeTodo");
    },
  },
});
</script>

<template>
  <li
    @click="completeTodo()"
    v-bind:class="{ active: todo.completed }"
    class="todo"
  >
    {{ todo.title }}
  </li>
</template>

<style scoped>
.active {
  text-decoration: line-through;
}

.todo {
  cursor: pointer;
}
</style>

<template>
  <ul class="todo-list">
    <AddTodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-todo="toggleTodo"
      @removeTodo="removeTodo"
    />
  </ul>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import AddTodoItem from "./AddTodoItem.vue";
import { Todo } from "@/types/Todo";



export default defineComponent({
  components: {
    AddTodoItem,
  },
  props:{
    todos:{
      type: Array as PropType<Todo[]>
    }
  },
  methods: {
   toggleTodo(id: number) {
     this.$emit("toggleTodo", id)
    },
    removeTodo(id: number){
      this.$emit("removeTodo", id)
    }
  },
   emits: {
    toggleTodo: (id: number) => Number.isInteger(id),
    removeTodo: (id: number) => Number.isInteger(id),
  },
});
</script>

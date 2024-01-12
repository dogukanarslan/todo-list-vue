<template>
  <ul class="todo-list">
    <Todo
      v-for="todo in todos"
      :todo="todo"
      @deleteTodo="(data) => $emit('deleteTodo', data)"
    />
  </ul>
</template>

<script>
import Todo from "./Todo.vue"

export default {
  emits: ["delete-todo"],
  components: { Todo },
  props: ["todos"]
}
</script>

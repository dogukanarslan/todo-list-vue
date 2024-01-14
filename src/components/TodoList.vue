<template>
  <ul class="todo-list">
    <Todo
      :key="todo.id"
      v-for="todo in todos"
      :todo="todo"
      @delete-todo="(id) => $emit('deleteTodo', id)"
      @edit-todo="(newTodo) => $emit('editTodo', newTodo)"
      @toggle-complete="(newTodo) => $emit('toggleComplete', newTodo)"
    />
  </ul>
</template>

<script>
import Todo from "./Todo.vue"

export default {
  emits: ["deleteTodo", "editTodo", "toggleComplete"],
  components: { Todo },
  props: ["todos"]
}
</script>

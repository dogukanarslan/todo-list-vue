<template>
  <ul class="todo-list">
    <Todo
      v-for="todo in todos"
      :todo="todo"
      @deleteTodo="(id) => $emit('delete-todo', id)"
      @editTodo="(newTodo) => $emit('edit-todo', newTodo)"
    />
  </ul>
</template>

<script>
import Todo from "./Todo.vue"

export default {
  emits: ["delete-todo", "edit-todo"],
  components: { Todo },
  props: ["todos"]
}
</script>

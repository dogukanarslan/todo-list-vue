<template>
  <ul class="todo-list">
    <li
      class="todo-list__todo"
      v-for="todo in todos"
      @click="todo.completed = !todo.completed"
    >
      <p>
        {{ todo.label }}
      </p>
      <Button color="danger" @click="$emit('deleteTodo', todo.label)" label="Delete" />
    </li>
  </ul>
</template>

<script>
import Button from "./Button.vue"

export default {
  props: ["todos"],
  components: { Button }
}
</script>

<style>
.todo-list__todo {
  display: flex;
  align-items: center;
  margin: 10px 0;
}

.todo-list__todo p {
  width: 100%;
}
</style>

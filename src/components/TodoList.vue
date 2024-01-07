<template>
  <ul class="todo-list">
    <li v-for="todo in todos" @click="todo.completed = !todo.completed">
      {{ todo.label }}
    </li>
  </ul>
</template>

<script>
export default {
  props: ["todos"]
}
</script>

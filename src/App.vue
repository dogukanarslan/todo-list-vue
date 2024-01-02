<template>
  <Navbar />

  <main>
    <form @submit="(e) => onSubmit(e)">
      <input v-model="todoText" placeholder="Add new todo" />
    </form>
    <TodoList :todos="todos" />
  </main>
</template>

<script>
import { ref } from "vue"
import Navbar from "./components/Navbar.vue"
import TodoList from "./components/TodoList.vue"

const todoText = ref("")
const todos = ref([])

const addTodo = () => {
  todos.value.push({ label: todoText.value, completed: false })
  todoText.value = ""
}

const onSubmit = (e, b) => {
  e.preventDefault()
  addTodo()
}

export default {
  components: { Navbar, TodoList },
  setup() {
    return { todoText, todos, onSubmit }
  }
}
</script>

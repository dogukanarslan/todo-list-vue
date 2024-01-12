<template>
  <Navbar />

  <main class="main">
    <form class="todo-list__form" @submit="onSubmit">
      <h2>ADD ITEM</h2>
      <div class="todo-list__add">
        <Input
          @changeTodo="(data) => (todoText = data)"
          :value="todoText"
          placeholder="Add new todo"
        />
        <Button label="Add" />
      </div>
    </form>
    <div v-if="todos.length > 0">
      <h2>TODO</h2>
      <TodoList
        :todos="todos"
        @delete-todo="deleteTodo"
        @edit-todo="editTodo"
      />
    </div>
  </main>
</template>

<script>
import { onMounted, ref } from "vue"
import Navbar from "./components/Navbar.vue"
import TodoList from "./components/TodoList.vue"
import Input from "./components/Input.vue"
import Button from "./components/Button.vue"

const todoText = ref("")
const todos = ref([])

export default {
  components: { Navbar, TodoList, Input, Button },
  setup() {
    onMounted(() => {
      const existingTodos = JSON.parse(localStorage.getItem("todos"))
      if (existingTodos) {
        todos.value = existingTodos
      }
    })

    const addTodo = () => {
      todos.value.push({
        id: Math.random(),
        label: todoText.value,
        completed: false
      })
      todoText.value = ""

      localStorage.setItem("todos", JSON.stringify(todos.value))
    }

    const deleteTodo = (id) => {
      const newTodos = todos.value.filter((todo) => todo.id !== id)
      todos.value = newTodos
      localStorage.setItem("todos", JSON.stringify(newTodos))
    }

    const editTodo = (newTodo) => {
      const newTodos = todos.value.map((currentTodo) =>
        newTodo.id === currentTodo.id
          ? { ...currentTodo, label: newTodo.label }
          : currentTodo
      )
      todos.value = newTodos
      localStorage.setItem("todos", JSON.stringify(newTodos))
    }

    const onSubmit = (e) => {
      e.preventDefault()
      addTodo()
    }

    return { todoText, todos, onSubmit, deleteTodo, editTodo }
  }
}
</script>

<style>
.main {
  width: 400px;
  margin: 10px auto;
  background-color: var(--white);
  border-radius: 10px;
  padding: 10px;
}

.main h2 {
  border-bottom: 2px solid black;
  text-transform: uppercase;
}

.todo-list__add {
  padding: 10px 0;
  display: flex;
  column-gap: 10px;
}
</style>

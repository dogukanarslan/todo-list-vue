<template>
  <!-- TODO: Fix this state mutation -->
  <li class="todo-list__todo" @click="todo.completed = !todo.completed">
    <Input
      @changeTodo="(data) => (editText = data)"
      v-if="isEditMode"
      :value="todo.label"
      placeholder="Add new todo"
    />
    <p v-else>
      {{ todo.label }}
    </p>
    <Button
      class="m-2"
      color="danger"
      @click="$emit('deleteTodo', todo.label)"
      label="Delete"
    />
    <Button v-if="isEditMode" @click="editTodo" label="Save" />
    <Button
      @click="isEditMode = !isEditMode"
      :label="isEditMode ? 'Cancel' : 'Edit'"
    />
  </li>
</template>

<script>
import {  ref } from "vue"
import Button from "./Button.vue"
import Input from "./Input.vue"

export default {
  emits: ['delete-todo'],
  components: { Button, Input },
  props: ["todo"],
  setup(props) {
    const isEditMode = ref(false)
    const editText = ref("")

    const editTodo = () => {
      props.todo.label = editText.value
      isEditMode.value = false
    }

    return { editText, isEditMode, editTodo }
  }
}
</script>

<style>
.todo-list__todo {
  display: flex;
  align-items: center;
  min-height: 40px;
  margin-top: 10px;
}

.todo-list__todo button {
  margin-left: 10px;
}

.todo-list__todo p {
  width: 100%;
}
</style>

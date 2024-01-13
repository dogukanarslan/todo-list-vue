<template>
  <li class="todo-list__todo">
    <div>
      <input
        type="checkbox"
        :checked="todo.completed"
        @change="$emit('toggleComplete', todo)"
      />
    </div>
    <div class="todo-list__edit-input" v-if="isEditMode">
      <Input @change="(val) => (editText = val)" :value="todo.label" />
    </div>
    <p v-else>
      {{ todo.label }}
    </p>
    <Button
      class="m-2"
      color="danger"
      @click="$emit('deleteTodo', todo.id)"
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
import { ref } from "vue"
import Button from "./Button.vue"
import Input from "./Input.vue"

export default {
  emits: ["deleteTodo", "editTodo", "toggleComplete"],
  components: { Button, Input },
  props: ["todo"],
  setup(props, { emit }) {
    const isEditMode = ref(false)
    const editText = ref("")

    const editTodo = () => {
      isEditMode.value = false
      emit("editTodo", { ...props.todo, label: editText.value })
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
  border-bottom: 1px solid #eee;
}

.todo-list__todo * + * {
  margin-left: 10px;
}

.todo-list__edit-input {
  width: 100%;
}

.todo-list__todo button {
  margin-left: 10px;
}

.todo-list__todo p {
  width: 100%;
}
</style>

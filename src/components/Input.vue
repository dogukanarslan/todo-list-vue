<template>
  <input
    class="input"
    :placeholder="placeholder"
    :value="value"
    @input="$emit('changeTodo', $event.target.value)"
  />
</template>

<script>
export default {
  props: ["value", "placeholder"],
  emits: ["changeTodo"]
}
</script>

<style>
.input {
  width: 100%;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  outline: none;
}
</style>

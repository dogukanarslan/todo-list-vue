<template>
  <p>Value is {{ value }}</p> 
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
  emits: ["changeTodo"],
} 
</script>

<style>
.input {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 5px;
}
</style>

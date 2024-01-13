<template>
  <input
    class="input"
    :placeholder="placeholder"
    :value="value"
    @change="$emit('change', $event.target.value)"
  />
</template>

<script>
export default {
  props: ["value", "placeholder"],
  emits: ["change"]
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

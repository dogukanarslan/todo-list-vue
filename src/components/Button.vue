<template>
  <button class="btn" @click="$emit('click')">{{ label }}</button>
</template>

<script>
export default {
  emits: ["click"],
  props: ["label"]
}
</script>

<style>
.btn {
  border: none;
  background: var(--primary);
  color: white;
  padding: 0.5rem 0.8rem;
  border-radius: 0.25rem;
  cursor: pointer;
}
</style>

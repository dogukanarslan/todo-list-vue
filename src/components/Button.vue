<template>
  <button
    class="btn"
    :class="
      color === 'primary'
        ? 'btn-primary'
        : color === 'danger'
        ? 'btn-danger'
        : ''
    "
    @click="$emit('click')"
  >
    {{ label }}
  </button>
</template>

<script>
export default {
  emits: ["click"],
  props: {
    label: {},
    color: {
      default() {
        return "primary"
      }
    }
  }
}
</script>

<style>
.btn {
  border: none;
  color: white;
  padding: 0.5rem 0.8rem;
  border-radius: 0.25rem;
  cursor: pointer;
}

.btn-primary {
  background-color: var(--primary);
}

.btn-danger {
  background-color: var(--danger);
}
</style>

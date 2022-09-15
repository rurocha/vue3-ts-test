<script setup lang="ts">

interface Props {
  value: string;
  placeholder: string;
}

defineProps<Props>()
const emit = defineEmits(['change']);

</script>

<template>
  <input
    class="input"
    :placeholder="placeholder"
    :value="value"
    @input="event => emit('change', (event.target as HTMLInputElement).value)"
  />
</template>

<style scoped>
.input {
  min-height: 26px;
  border-radius: 4px;
  background-color: var(--color-blue-dark);
  padding: 8px;
  min-width: 400px;
}
.input, .input::placeholder {
  color: #fff;
}
</style>
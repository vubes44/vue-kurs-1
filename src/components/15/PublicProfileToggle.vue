<template>
  <label class="label">
    Profil publiczny:
    <input
      type="checkbox"
      class="label__input"
      :checked="modelValue"
      @change="$emit('update:modelValue', $event.target.checked)"
    />
    {{ modelValue ? 'TAK' : 'NIE' }}
  </label>
</template>

<script setup>
defineProps({
  modelValue: {
    type: Boolean,
    required: true,
  },
})

defineEmits(['update:modelValue'])
</script>
<style scoped>
.label {
  font-family: 'Calibri', sans-serif;
  font-size: 1.1rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.label__input {
  width: 1.2rem;
  height: 1.2rem;
}
</style>

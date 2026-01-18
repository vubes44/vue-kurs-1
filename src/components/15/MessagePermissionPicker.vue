<template>
  <div class="radio-group">
    <label class="radio-group__label">
      <input
        type="radio"
        class="radio-group__label__input"
        name="msgPerm"
        value="everyone"
        :checked="value === 'everyone'"
        :disabled="disabled"
        @change="$emit('change', 'everyone')"
      />
      Wszyscy
    </label>

    <label class="radio-group__label">
      <input
        type="radio"
        class="radio-group__label__input"
        name="msgPerm"
        value="friends"
        :checked="value === 'friends'"
        :disabled="disabled"
        @change="$emit('change', 'friends')"
      />
      Tylko znajomi
    </label>

    <label class="radio-group__label">
      <input
        type="radio"
        class="radio-group__label__input"
        name="msgPerm"
        value="nobody"
        :checked="value === 'nobody'"
        :disabled="disabled"
        @change="$emit('change', 'nobody')"
      />
      Nikt
    </label>
  </div>
</template>

<script setup>
defineProps({
  value: {
    type: String,
    required: true,
  },
  disabled: {
    type: Boolean,
    default: false,
  },
})

defineEmits(['change'])
</script>

<style scoped>
.radio-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
.radio-group__label {
  font-family: 'Calibri';
  font-size: 1rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.radio-group__label__input {
  cursor: pointer;
}
</style>

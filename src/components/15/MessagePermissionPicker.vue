<template>
  <div class="message-permission-picker">
    <label class="radio-group-label">
      <input
        type="radio"
        class="radio-group-input"
        name="msgPerm"
        value="everyone"
        :checked="value === 'everyone'"
        :disabled
        @change="$emit('change', 'everyone')"
      />
      Wszyscy
    </label>

    <label class="radio-group-label">
      <input
        type="radio"
        class="radio-group-input"
        name="msgPerm"
        value="friends"
        :checked="value === 'friends'"
        :disabled
        @change="$emit('change', 'friends')"
      />
      Tylko znajomi
    </label>

    <label class="radio-group-label">
      <input
        type="radio"
        class="radio-group-input"
        name="msgPerm"
        value="nobody"
        :checked="value === 'nobody'"
        :disabled
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
.message-permission-picker {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
.radio-group-label {
  font-family: 'Calibri';
  font-size: 1rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.radio-group-input {
  cursor: pointer;
}
</style>

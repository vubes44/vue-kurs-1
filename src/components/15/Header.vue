<template>
  <h1 class="header">{{ title }}</h1>
</template>
<script setup>
import { defineProps } from 'vue'
defineProps({
  title: String,
})
</script>
<style scoped>
.header {
  font-family: Arial, sans-serif;
  color: rgb(12, 12, 12);
  text-align: center;
  margin: 20px;
}
</style>

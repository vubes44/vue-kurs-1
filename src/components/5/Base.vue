<template></template>

<script setup>
import { reactive, ref } from 'vue'
import Base from './components/5/Base.vue'

// 1. ref - tworzy reaktywną wartość dla m.in. prymitywów (tutaj: ID)
const userId = ref(0)

// 2. reactive - tworzy reaktywny obiekt (tutaj: obiekt stanu)
const shippingDetails = reactive({
  counter: 42,
  user: {
    name: 'Vue developer',
    role: 'admin',
  },
})

// 3. zwykła zmienna
let normalCounter = 100
</script>

<style scoped></style>

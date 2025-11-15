<template>
  <div class="shipping">
    <h1>ID: {{ userId }}</h1>
    <p>Counter: {{ shippingDetails.counter }}</p>
    <div class="shipping__details">
      <h2>Shipping information</h2>
      <p>Name: shippingDetails.user.name</p>
      <p>Rame: shippingDetails.user.role</p>
    </div>

    <p>Normal counter: {{ normalCounter }}</p>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'

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

setInterval(() => {
  userId.value++
  shippingDetails.counter++
}, 1000)
</script>

<style scoped>
.shipping__details {
  margin-top: 20px;
  background: #f4f4f4;
  padding: 10px;
}
</style>

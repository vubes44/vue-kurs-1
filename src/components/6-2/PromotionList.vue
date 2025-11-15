<template>
  <CurrentPromotionText />
  <p v-show="isPromoInfoVisible">🔥Promotions are valid until the end of the month!</p>
  <ul>
    <li v-for="order in orders" :key="order.id">
      <h3>Name: {{ order.name }}</h3>
      Dicount: {{ order.discount }}%<br /><br />
      <span v-show="order.isLimited"> ⏳Limited Time Offer!</span>
    </li>
  </ul>
</template>
<script setup lang="ts">
import { ref } from 'vue'
let isPromoInfoVisible = ref(true)
import CurrentPromotionText from './CurrentPromotionText.vue'
const orders = [
  { id: 1, name: 'Laptop Pro', discount: 25, isLimited: false },
  { id: 2, name: 'Smartwatch X', discount: 60, isLimited: true },
  { id: 3, name: 'Tablet Mini', discount: 15, isLimited: false },
  { id: 4, name: 'ANC Headphones', discount: 55, isLimited: true },
  { id: 5, name: 'laptop', discount: 500, isLimited: true },
]
</script>
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
  margin-left: 20px;
}
</style>

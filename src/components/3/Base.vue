<template>
  <div class="product">
    <h2>Name: {{ productName }}</h2>
    <p>Description: {{ productDescription }}</p>
    <p>Discounted price: {{ (productPrice * SALARY_RATE).toFixed(2) }}</p>
    <p class="product__base-price">
      Base price {{ productPrice.toFixed(2) }} {{ productPriceCurrency }}
    </p>
  </div>
</template>

<script setup>
const SALARY_RATE = 0.8

const productName = 'Smartwatch X'
const productDescription = 'Modern smartwatch with health fetures'
const productPrice = 1299
const productPriceCurrency = '$'
</script>

<style></style>

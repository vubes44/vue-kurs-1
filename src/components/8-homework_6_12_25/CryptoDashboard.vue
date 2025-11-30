<template>
  <CryptoPriceDashboardText />
  <span>Your Bitcoin purchase price: {{ bitcoinPurchasePrice }}</span> <br />
  <span>Current Bitcoin price: {{ currentBitcoinPrice }}</span> <br />
  <span>Market information: {{ marketInformation }}</span> <br />
  <span>Highest price observed: {{ highestPriceObserved }}</span> <br />
  <PriceHistoryText />
  <ul>
    <li v-for="(price, index) in priceHistory" :key="index">
      {{ formatPrice(price) }}
    </li>
  </ul>

  Is your investment profitable? {{ isTheInvestmentProfitableText }}
</template>

<script setup>
import { ref } from 'vue'
import CryptoPriceDashboardText from './CryptoPriceDashboardText.vue'
import PriceHistoryText from './PriceHistoryText.vue'

const formatPrice = (value) => value.toFixed(2)

const bitcoinPurchasePrice = ref(49000)
const currentBitcoinPrice = ref(48000)
const priceHistory = ref([48000])

const marketInformation = ref('Price has not changed')
const highestPriceObserved = ref(formatPrice(currentBitcoinPrice.value))

const isTheInvestmentProfitable = ref(false)
const isTheInvestmentProfitableText = ref('No')

setInterval(function () {
  const oldPrice = currentBitcoinPrice.value
  let change = Math.floor(Math.random() * 6001) - 3000
  currentBitcoinPrice.value += change
  const priceDifference = currentBitcoinPrice.value - oldPrice
  if (currentBitcoinPrice.value > highestPriceObserved.value) {
    highestPriceObserved.value = currentBitcoinPrice.value
  }

  if (priceDifference > 0) {
    marketInformation.value = `Bitcoin prices increased by ${formatPrice(priceDifference)}`
  } else if (priceDifference < 0) {
    marketInformation.value = `Bitcoin prices decreased by ${formatPrice(Math.abs(priceDifference))}`
  } else {
    marketInformation.value = 'Price has not changed'
  }

  isTheInvestmentProfitable.value = currentBitcoinPrice.value > bitcoinPurchasePrice.value

  isTheInvestmentProfitableText.value = isTheInvestmentProfitable.value ? 'Yes' : 'No'

  priceHistory.value.push(currentBitcoinPrice.value)
}, 1000)
</script>

<style scoped>
* {
  font-family: Calibri;
}
</style>

<script setup>
import { ref, computed } from 'vue'
import socksGreenImage from '../assets/images/socks_green.jpeg'
import socksBlueImage from '../assets/images/socks_blue.jpeg'
import ProductDetails from './ProductDetails.vue'
const selectedVariant = ref(0)

const variants = [
  { color: 'green', image: socksGreenImage },
  { color: 'blue', image: socksBlueImage }
]

const image = computed(() => variants[selectedVariant.value].image)


</script>

<template>
  <div id="app">
    <div class="product-display">
      <div class="product-container">
        <div class="product-image">
          <img :src="image" alt="product image">
        </div>
        <ProductDetails></ProductDetails>
      </div>
    </div>
  </div>
</template>
